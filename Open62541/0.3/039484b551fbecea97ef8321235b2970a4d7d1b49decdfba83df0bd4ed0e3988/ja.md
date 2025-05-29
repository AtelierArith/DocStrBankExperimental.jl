```julia
struct UA_EventFilterResult
```

フィールド:

  * `selectClauseResultsSize::UInt64`
  * `selectClauseResults::Ptr{UInt32}`
  * `selectClauseDiagnosticInfosSize::UInt64`
  * `selectClauseDiagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
  * `whereClauseResult::Open62541.UA_ContentFilterResult`
