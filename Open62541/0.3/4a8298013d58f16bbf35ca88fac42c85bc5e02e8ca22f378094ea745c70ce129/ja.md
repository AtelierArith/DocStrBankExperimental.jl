```julia
struct UA_SetTriggeringResponse
```

フィールド:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `addResultsSize::UInt64`
  * `addResults::Ptr{UInt32}`
  * `addDiagnosticInfosSize::UInt64`
  * `addDiagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
  * `removeResultsSize::UInt64`
  * `removeResults::Ptr{UInt32}`
  * `removeDiagnosticInfosSize::UInt64`
  * `removeDiagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
