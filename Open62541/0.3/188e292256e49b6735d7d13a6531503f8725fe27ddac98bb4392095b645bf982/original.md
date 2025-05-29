```julia
struct UA_HistoryUpdateResult
```

Fields:

  * `statusCode::UInt32`
  * `operationResultsSize::UInt64`
  * `operationResults::Ptr{UInt32}`
  * `diagnosticInfosSize::UInt64`
  * `diagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
