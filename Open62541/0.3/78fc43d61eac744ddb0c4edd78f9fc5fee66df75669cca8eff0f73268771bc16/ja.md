```julia
struct UA_UpdateEventDetails
```

フィールド:

  * `nodeId::Open62541.UA_NodeId`
  * `performInsertReplace::Open62541.UA_PerformUpdateType`
  * `filter::Open62541.UA_EventFilter`
  * `eventDataSize::UInt64`
  * `eventData::Ptr{Open62541.UA_HistoryEventFieldList}`
