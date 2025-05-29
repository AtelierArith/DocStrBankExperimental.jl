```julia
struct UA_SetMonitoringModeRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `subscriptionId::UInt32`
  * `monitoringMode::Open62541.UA_MonitoringMode`
  * `monitoredItemIdsSize::UInt64`
  * `monitoredItemIds::Ptr{UInt32}`
