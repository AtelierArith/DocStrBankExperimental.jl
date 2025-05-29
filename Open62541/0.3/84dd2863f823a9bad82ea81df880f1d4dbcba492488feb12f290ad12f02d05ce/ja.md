```julia
struct UA_HistoryReadResult
```

フィールド:

  * `statusCode::UInt32`
  * `continuationPoint::Open62541.UA_String`
  * `historyData::Open62541.UA_ExtensionObject`
