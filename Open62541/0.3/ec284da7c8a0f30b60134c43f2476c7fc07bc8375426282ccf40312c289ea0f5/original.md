```
response::Ptr{UA_SetTriggeringResponse} = UA_Client_MonitoredItems_setTriggering(client::Ptr{UA_Client}, 
    request::Ptr{UA_SetTriggeringRequest}) 
```

uses the client API to set the monitoring mode on monitored items. Note that memory for the response is allocated by C and needs to be cleaned up using `UA_SetTriggeringResponse_delete(response)` after its use.

See also:

[Monitored item model at OPC Foundation](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1)

[SetTriggering at OPC Foundation](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.5)

[`UA_SetTriggeringRequest`](@ref)

[`UA_SetTriggeringResponse`](@ref)
