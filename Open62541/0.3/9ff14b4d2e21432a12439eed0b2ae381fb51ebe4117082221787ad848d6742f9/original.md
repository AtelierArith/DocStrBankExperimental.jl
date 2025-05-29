```
UA_ClientAsyncReadUserAccessLevelAttributeCallback_generate(f::Function)
```

creates a `UA_ClientAsyncReadUserAccessLevelAttributeCallback` that can be supplied as callback argument to `UA_Client_readUserAccessLevelAttribute_async`. The callback will be triggered once the read operation has been carried out.

`f` must be a Julia function with the following signature:

```
f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestid::UA_UInt32, 
    status::UA_StatusCode, useraccesslevel)::UA_Byte)::Nothing
```
