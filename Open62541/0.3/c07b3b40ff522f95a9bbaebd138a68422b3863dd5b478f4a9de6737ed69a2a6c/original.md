```
UA_Client_MonitoredItems_setTriggering_async(client::Ptr{UA_Client}, 
    request::Ptr{UA_SetTriggeringRequest},
    callback::UA_ClientAsyncServiceCallback,
    userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

uses the asynchronous client API to set the triggering on monitored items.

See also:

[Monitored item model at OPC Foundation](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1)

[Monitoring mode at OPC Foundation](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1.3)

[`UA_SetTriggeringRequest`](@ref)

[`UA_ClientAsyncServiceCallback_generate`](@ref)
