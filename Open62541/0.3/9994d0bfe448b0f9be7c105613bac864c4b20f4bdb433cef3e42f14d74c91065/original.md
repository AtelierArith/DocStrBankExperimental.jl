```
UA_Client_sendAsyncBrowseRequest(client::Ptr{UA_Client}, 
    request::Ptr{UA_BrowseRequest},
    readCallback::UA_ClientAsyncBrowseCallback,
    userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

uses the asynchronous client API to send a browse request.

See also:

[`UA_BrowseRequest`](@ref)

[`UA_ClientAsyncBrowseCallback_generate`](@ref)
