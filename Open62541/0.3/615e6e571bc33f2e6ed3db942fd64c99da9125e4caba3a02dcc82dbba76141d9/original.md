```
UA_Client_sendAsyncWriteRequest(client::Ptr{UA_Client}, 
    request::Ptr{UA_WriteRequest},
    readCallback::UA_ClientAsyncWriteCallback,
    userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

uses the asynchronous client API to send a write request.

See also:

[`UA_WriteRequest`](@ref)

[`UA_ClientAsyncWriteCallback_generate`](@ref)
