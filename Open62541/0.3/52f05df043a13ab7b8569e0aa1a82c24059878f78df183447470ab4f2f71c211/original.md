```
UA_ValueCallback_onRead_generate(f::Function)
```

creates a function pointer for the `onRead` field of a `UA_ValueCallback` object.

`f` must be a Julia function with the following signature:

```
f(server::Ptr{UA_Server}, sessionid::Ptr{UA_NodeId}), sessioncontext::Ptr{Cvoid},
        nodeid::Ptr{Cvoid}, nodecontext::Ptr{Cvoid}, range::Ptr{UA_NumericRange}, 
        data::Ptr{UA_DataValue})::Nothing
```
