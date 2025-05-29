```julia
struct UA_CreateMonitoredItemsRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `subscriptionId::UInt32`
  * `timestampsToReturn::Open62541.UA_TimestampsToReturn`
  * `itemsToCreateSize::UInt64`
  * `itemsToCreate::Ptr{Open62541.UA_MonitoredItemCreateRequest}`
