```julia
struct UA_DeleteMonitoredItemsRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `subscriptionId::UInt32`
  * `monitoredItemIdsSize::UInt64`
  * `monitoredItemIds::Ptr{UInt32}`
