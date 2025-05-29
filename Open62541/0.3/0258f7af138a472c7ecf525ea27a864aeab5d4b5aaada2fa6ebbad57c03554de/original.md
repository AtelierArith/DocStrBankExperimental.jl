```
JUA_Client_connect(client::JUA_Client, endpointurl::AbstractString)::UA_StatusCode
```

connect the `client` to the server with `endpointurl`. This is an anonymous connection, i.e., no username or password are used (some servers do not allow this).
