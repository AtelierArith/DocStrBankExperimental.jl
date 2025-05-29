```
get_meta(table; base, api)
```

Get the metadata for a given `table`. The result is a dict with the keys `"TableInfos"`, `"DataProperties"` and all the classifications.

Optional parameters are:

  * base::String, basename of the OData3 server
  * api::String, path part of the OData3 server for regular data
