```
UA_Client_call_async(client::Ptr{UA_Client}, objectId::Ptr{UA_NodeId}, methodId::Ptr{UA_NodeId},
    inputSize::Csize_t, input::Ptr{UA_Variant}, callback::UA_ClientAsyncCallCallback, 
    userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

uses the asynchronous client API to call the method `methodId` on the server the client is connected with.

See also: [`UA_ClientAsyncCallCallback_generate`](@ref)
