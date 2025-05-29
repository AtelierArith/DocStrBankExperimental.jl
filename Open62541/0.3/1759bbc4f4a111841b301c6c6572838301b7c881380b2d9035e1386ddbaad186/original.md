```julia
struct UA_AggregateFilter
```

Fields:

  * `startTime::Int64`
  * `aggregateType::Open62541.UA_NodeId`
  * `processingInterval::Float64`
  * `aggregateConfiguration::Open62541.UA_AggregateConfiguration`
