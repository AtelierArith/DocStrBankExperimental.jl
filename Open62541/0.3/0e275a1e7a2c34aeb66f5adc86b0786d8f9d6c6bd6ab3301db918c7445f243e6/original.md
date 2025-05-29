```
UA_ClientAsyncReadWriteMaskAttributeCallback_generate(f::Function)
```

creates a `UA_ClientAsyncReadWriteMaskAttributeCallback` that can be supplied as callback argument to `UA_Client_readWriteMaskAttribute_async`. The callback will be triggered once the read operation has been carried out.

`f` must be a Julia function with the following signature:

```
f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestid::UA_UInt32, 
    status::UA_StatusCode, writeMask)::UA_UInt32)::Nothing
```
