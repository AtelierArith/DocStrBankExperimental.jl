```
response::Ptr{UA_SetMonitoringModeResponse} = UA_Client_MonitoredItems_setMonitoringMode(client::Ptr{UA_Client}, 
    request::Ptr{UA_SetMonitoringModeRequest})
```

uses the client API to set the monitoring mode on monitored items. Note that memory for the response is allocated by C and needs to be cleaned up using `UA_SetMonitoringModeResponse_delete(response)` after its use.

See also:

[Monitored item model at OPC Foundation](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1)

[Monitoring mode at OPC Foundation](https://reference.opcfoundation.org/Core/Part4/v105/docs/5.12.1.3)

[`UA_SetMonitoringModeRequest`](@ref)

[`UA_SetMonitoringModeResponse`](@ref)
