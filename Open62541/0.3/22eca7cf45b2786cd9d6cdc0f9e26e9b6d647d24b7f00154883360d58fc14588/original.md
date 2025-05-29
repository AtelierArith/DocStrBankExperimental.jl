```julia
struct UA_DataChangeNotification
```

Fields:

  * `monitoredItemsSize::UInt64`
  * `monitoredItems::Ptr{Open62541.UA_MonitoredItemNotification}`
  * `diagnosticInfosSize::UInt64`
  * `diagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
