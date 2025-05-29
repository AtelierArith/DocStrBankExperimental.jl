```julia
struct UA_HistoryUpdateRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `historyUpdateDetailsSize::UInt64`
  * `historyUpdateDetails::Ptr{Open62541.UA_ExtensionObject}`
