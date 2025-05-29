```
DBInterface.execute(conn::SQLConnection, sql::SQLNode; params...)
DBInterface.execute(conn::SQLConnection, sql::SQLClause; params...)
```

Serialize and execute the query node.
