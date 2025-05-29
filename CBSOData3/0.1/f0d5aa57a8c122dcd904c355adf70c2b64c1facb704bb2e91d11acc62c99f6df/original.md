```
get_tables(base, catalog)
```

Get all the tables in the catalog as a list of dicts. The `Identifier` can be  used to get the actual data. If no parameters are given, the data is retrieved from the (CBS)[https://www.cbs.nl] OData3 portal.

The optional parameters are:

  * base::String, basename of the OData3 server
  * catalog::String, path part of the OData3 server for catalog information
