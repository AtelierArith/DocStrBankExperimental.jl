```
request::Ptr{UA_MonitoredItemCreateRequest} = UA_MonitoredItemCreateRequest_default(nodeId::Ptr{UA_NodeId})
```

create a monitored item create request that monitors `nodeId`. The monitored item properties are set to their default values.

Note that memory for the request is allocated by C and needs to be cleaned up by using `UA_MonitoredItemCreateRequest_delete(request)` after its use.

See also:

[`UA_MonitoredItemCreateRequest`](@ref)
