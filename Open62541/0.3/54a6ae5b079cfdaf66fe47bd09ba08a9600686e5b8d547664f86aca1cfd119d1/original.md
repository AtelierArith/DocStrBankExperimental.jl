```
UA_DataSourceCallback_read_generate(f::Function)
```

creates a function pointer for the `read` field of a `UA_DataSource` object.

`f` must be a Julia function with the following signature:

```
f(server::Ptr{UA_Server}, sessionid::Ptr{UA_NodeId}), sessioncontext::Ptr{Cvoid},
        nodeid::Ptr{Cvoid}, nodecontext::Ptr{Cvoid}, includesourcetimestamp::UA_Boolean, 
        range::Ptr{UA_NumericRange}, data::Ptr{UA_DataValue})::UA_StatusCode
```
