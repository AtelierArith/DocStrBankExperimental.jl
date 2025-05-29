```
UA_ClientAsyncReadAccessLevelAttributeCallback_generate(f::Function)
```

creates a `UA_ClientAsyncReadAccessLevelAttributeCallback` that can be supplied as callback argument to `UA_Client_readAccessLevelAttribute_async`. The callback will be triggered once the read operation has been carried out.

`f` must be a Julia function with the following signature:

```
f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestid::UA_UInt32, 
    status::UA_StatusCode, accesslevel)::UA_Byte)::Nothing
```
