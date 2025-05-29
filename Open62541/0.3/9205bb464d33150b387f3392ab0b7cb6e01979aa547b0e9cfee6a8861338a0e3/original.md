```julia
struct UA_HistoryReadRequest
```

Fields:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `historyReadDetails::Open62541.UA_ExtensionObject`
  * `timestampsToReturn::Open62541.UA_TimestampsToReturn`
  * `releaseContinuationPoints::Bool`
  * `nodesToReadSize::UInt64`
  * `nodesToRead::Ptr{Open62541.UA_HistoryReadValueId}`
