# Audit, monitor and receive notifications on table change from SQL Server

SqlTableDependency is a high-level C# component to used to audit, monitor and receive notifications on SQL Server's record table changes.

For any record table change, insert update or delete, a notification *containing values for the record **inserted**, **changed** or **deleted** is received from SqlTableDependency. This notification contains the update values int the database table.

Compared to Microsoft ADO.NET SqlDependency class, this tracking change system has the advantage of avoid a database select to retrieve updated table record state, because this latest table status is delivered by the received notification.

[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/FBkkdCuTO7g/0.jpg)](http://www.youtube.com/watch?v=FBkkdCuTO7g)

## Track record table change
If we want **get alert about record table changes** without paying attention to the underlying SQL Server infrastructure then SqlTableDependency's record table change notifications will do that for us. Using notifications, an application can **detect table record changes** saving us from having to continuously re-query the database to get new values.

SqlTableDependency's record change audit, provides the low-level implementation to receive database notifications creating SQL Server trigger, queue and service broker that immediately notify us when any record table changes happens.

For any record change, SqlTableDependency's event handler will get a notification containing modified table record values as well as the insert, update, delete operation type executed on our table.

Basically, it is an enhancement of .NET SqlDepenency with the advantage of send events containing values for the record inserted, changed or deleted, as well as the DML operation (insert/delete/update) executed on the table. This is the real difference with. NET SqlDepenency: this class, in fact, does not tell you what data was changed on the database.

## Requirements
When you use notifications, you must be sure to enable Service Broker for the database. To do that you can use the following command:
```SQL
ALTER DATABASE MyDatabase SET ENABLE_BROKER
```
Also case user specified in connection string is not DBO or has not db_owner role, he must have the following GRANT permissions:
* ALTER
* CONNECT
* CONTROL
* CREATE CONTRACT
* CREATE MESSAGE TYPE
* CREATE PROCEDURE
* CREATE QUEUE
* CREATE SERVICE
* EXECUTE
* SELECT
* SUBSCRIBE QUERY NOTIFICATIONS
* VIEW DATABASE STATE
* VIEW DEFINITION