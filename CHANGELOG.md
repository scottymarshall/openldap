openldap Cookbook CHANGELOG
===========================
This file is used to list changes made in each version of the openldap cookbook.

v2.2.2
-------
- fixes for chef13

Unreleased
----
This version has several major breaking changes that you will need to be aware of.
- This auth recipe no longer includes the nscd and openssh cookbooks.  This gives users more control over how they setup their environment. If you want these you'll need to include them yourself in a base role.  If they're included in the node's runlist the appropriate nscd/sshd restarts will still occur as pam / nsswitch configs are updated
- pam.d files are no longer cookbook files and are instead generated via a hash which allows as many or as few files to be managed as you wish.  See the readme for more information
- A client config and server config hash have been added to add arbitrary files to the ldap.config and slapd.config files.  This eliminates much of the need for forking this cookbook to meet your environment's needs.  See the readme for detailed information on how these hashes are converted to ldap configs.

v2.2.0 (2015-04-16)
-------------------
- Added support for FreeBSD
- Improved support for RHEL platforms
- Removed the attributes from the metadata.rb file since they were outdated


v2.1.0 (2015-03-10)
-------------------
- Resolve the one and only Food Critic warning
- Remove legacy LDAP Apache2 attributes that aren't used in this cookbook or in the Apache2 cookbook
- Add an attribute for schemas to enable in the slapd config
- Add an attribute for the modules to load in the slapd config
- Make the cn used an attribute

v2.0.0 (2015-03-06)
-------------------
- Added URI to the client config so clients can communicate with the LDAP server
- Change all package resource actions from upgrade -> install and introduce and attribute if you want to change it back.  Upgrading openldap when a new package comes out is not a desired action on production systems.
- Update the "Generated by Chef for xyz" comment blocks in the config templates to be consistent.  This will result in config changes / service restarts due to notification
- Install the most recent version of the Berkeley DB utils package.  This adds support for Trusty and RHEL, but will result in a newer version of the bd-util package being installed on Precise systems.
- Added new attributes to set the cookbook and source path for the SSL keys and certs.  This reduces the need to fork / modify this cookbook
- Added a new attribute for controlling the log level of the server
- Make the ldap client package an attribute with support for RHEL
- Fix the search logic in the slave recipe to not fail
- Converted the cookbook to platform_family to better support Ubuntu.  This means the cookbook will no longer work on Chef versions prior to 0.10.10
- Updated Gemfile with up to date dependency versions
- Updated Contributing doc to match the current process
- Added a chefignore file to prevent ds_store files from ending up in /usr/local/bin
- Switched all modes to strings to preserve the leading 0
- Added a rubocop.yml file and resolved the majority of rubocop complaints
- Updated platforms in the kitchen.yml file

v1.12.13 (2015-02-18)
---------------------
- reverting OpenSSL module namespace change

v1.12.12 (2015-02-17)
---------------------
- Updating to work with latest openssl cookbook

v1.12.10 (2014-04-09)
---------------------
- [COOK-4239] - Service enable/start resource moved to end
- [COOK-4239] - Fix sslfiles + ubuntu fix


v1.12.8 (2014-01-03)
--------------------
Merged nildomain branch


v1.12.6 (2014-01-03)
--------------------
adding checks for node['domain'].nil? in attributes


v1.12.4
-------

- [COOK-3772] - nscd clears don't work
- [COOK-411]  - Openldap authentication should validate server certificate


v1.12.2
-------
### Improvement
- **[COOK-3699](https://tickets.chef.io/browse/COOK-3699)** - OpenLDAP Cookbooks - add extra options


u tv0.12.0
-------
### New Feature
- **[COOK-3561](https://tickets.chef.io/browse/COOK-3561)** - Support out of band SSL certificates in openldap::server

### Bug
- **[COOK-3548](https://tickets.chef.io/browse/COOK-3548)** - Fix an issue where preseeding may fail if directory does not exist
- **[COOK-3543](https://tickets.chef.io/browse/COOK-3543)** - Do not try to set up as a slave
- **[COOK-3351](https://tickets.chef.io/browse/COOK-3351)** - Fix a typo in `ldap-ldap.conf.erb` template


v0.11.4
-------
### Bug
- **[COOK-3348](https://tickets.chef.io/browse/COOK-3348)** - Fix typo in default attributes

v0.11.2
-------
### Bug
- [COOK-2496]: openldap: rootpw is badly set in attributes file
- [COOK-2970]: openldap cookbook has foodcritic failures

v0.11.0
-------
- [COOK-1588] - general cleanup/improvements
- [COOK-1985] - attributes file has a search method

v0.10.0
-------
- [COOK-307] - create directory with attribute

v0.9.4
-------
- Initial/Current release
