```julia
struct UA_EventFilter
```

フィールド:

  * `selectClausesSize::UInt64`
  * `selectClauses::Ptr{Open62541.UA_SimpleAttributeOperand}`
  * `whereClause::Open62541.UA_ContentFilter`
