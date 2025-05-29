```julia
struct UA_HistorizingNodeIdSettings
```

フィールド:

  * `historizingBackend::Open62541.UA_HistoryDataBackend`
  * `maxHistoryDataResponseSize::UInt64`
  * `historizingUpdateStrategy::Open62541.UA_HistorizingUpdateStrategy`
  * `pollingInterval::UInt64`
  * `userContext::Ptr{Nothing}`
