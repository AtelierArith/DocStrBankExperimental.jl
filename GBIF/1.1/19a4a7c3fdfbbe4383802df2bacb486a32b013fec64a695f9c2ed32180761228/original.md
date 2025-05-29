```
occurrence(key::String)
```

Returns a GBIF occurrence identified by a key. The key can be given as a string or as an integer (there is a second method for integer keys). In case the status of the HTTP request is anything other than 200 (success), this function *will* throw an error.
