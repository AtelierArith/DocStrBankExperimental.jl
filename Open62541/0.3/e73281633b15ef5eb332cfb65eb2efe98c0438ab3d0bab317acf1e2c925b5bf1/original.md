```
UA_Client_connectUsername(client::Ptr{UA_Client}, endpointurl::AbstractString, 
    username::AbstractString, password::AbstractString)::UA_StatusCode
```

connects the `client` to the server with endpoint URL `endpointurl` and supplies `username` and `password` as login credentials.
