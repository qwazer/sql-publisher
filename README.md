# sql-publisher

Maven plugin to help organize and publish sql script sets as maven artifact.

It will helpfull for teams, which devepoment process has

   * sql database development part
   * database change set can be issues as stanalone module or as dependency for one or several other modules
   * unpredictable release process, so developer don't know which version of module will be assigned to his currently resolving task, issue or bug 
   * fearsome database admin, that doesn't allow to install database scripts automatically and want to review all sql scripts before installing it

## sql-pulisher usage conditions and scenario

   * One project (or module) for all database changes
   * Scripts for resolved issued without fixversion number stored in *scripts pool* directory
   * Scripts for current version of database scripts set artifact stored (or moved from *scripts pool*) in *current version* directory
   * When `sql-publisher:release` target invoked it assigns current version of maven project to scripts in *current version* directory and assembly it in output folder. 
   Optionally it can apply different file transformations:
      * split every sql statement to single file
      * concatenate all sql scripts to single file
      * replace sql-statement delimeters with specified one
      * add custom statement to track and hold currently installed modules in database version table,
       for example `insert into module_version_table(module_name, version) values('x', 'y')`
   
## Benefits
   * Combination of sql-publisher with maven-release pluging will give automated database artifacts versioning
   * Produced artifacts can be used as *provided* dependency in other modules. 
   * Other modules can be extended to check database version table for requrement dependend database module is installed on currently operated database 
   
   //todo multi-modules
   
   
   
   

