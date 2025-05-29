```
UA_Client_sendAsyncReadRequest(client::Ptr{UA_Client}, 
    request::Ptr{UA_ReadRequest},
    readCallback::UA_ClientAsyncReadCallback,
    userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

uses the asynchronous client API to send a read request.

See also:

[`UA_ReadRequest`](@ref)

[`UA_ClientAsyncReadCallback_generate`](@ref)
