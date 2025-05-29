```julia
struct UA_ContentFilterResult
```

フィールド:

  * `elementResultsSize::UInt64`
  * `elementResults::Ptr{Open62541.UA_ContentFilterElementResult}`
  * `elementDiagnosticInfosSize::UInt64`
  * `elementDiagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
