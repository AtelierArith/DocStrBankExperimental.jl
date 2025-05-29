```julia
struct UA_FindServersOnNetworkRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `startingRecordId::UInt32`
  * `maxRecordsToReturn::UInt32`
  * `serverCapabilityFilterSize::UInt64`
  * `serverCapabilityFilter::Ptr{Open62541.UA_String}`
