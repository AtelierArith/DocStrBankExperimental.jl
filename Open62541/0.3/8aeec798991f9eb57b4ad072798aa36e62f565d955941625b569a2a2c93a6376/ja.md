```julia
struct UA_ModifyMonitoredItemsRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `subscriptionId::UInt32`
  * `timestampsToReturn::Open62541.UA_TimestampsToReturn`
  * `itemsToModifySize::UInt64`
  * `itemsToModify::Ptr{Open62541.UA_MonitoredItemModifyRequest}`
