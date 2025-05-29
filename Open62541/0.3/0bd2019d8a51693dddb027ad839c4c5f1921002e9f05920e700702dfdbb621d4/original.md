```
UA_ClientReadArrayDimensionsAttributeCallback_generate(f::Function)
```

creates a `UA_ClientReadArrayDimensionsAttributeCallback` that can be supplied as callback argument to `UA_Client_readUA_ClientReadArrayDimensionsAttribute_async`. The callback will be triggered once the read operation has been carried out.

`f` must be a Julia function with the following signature:

```
f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestid::UA_UInt32, 
    status::UA_StatusCode, arraydimensions)::UA_Variant)::Nothing
```
