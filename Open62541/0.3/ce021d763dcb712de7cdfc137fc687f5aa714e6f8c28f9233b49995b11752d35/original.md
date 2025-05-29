```
UA_ClientAsyncReadUserExecutableAttributeCallback_generate(f::Function)
```

creates a `UA_ClientAsyncReadUserExecutableAttributeCallback` that can be supplied as callback argument to `UA_Client_readUserExecutableAttribute_async`. The callback will be triggered once the read operation has been carried out.

`f` must be a Julia function with the following signature:

```
f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestid::UA_UInt32, 
    status::UA_StatusCode, userexecutable)::UA_Boolean)::Nothing
```
