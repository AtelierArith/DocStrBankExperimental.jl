```julia
struct UA_ReadProcessedDetails
```

Fields:

  * `startTime::Int64`
  * `endTime::Int64`
  * `processingInterval::Float64`
  * `aggregateTypeSize::UInt64`
  * `aggregateType::Ptr{Open62541.UA_NodeId}`
  * `aggregateConfiguration::Open62541.UA_AggregateConfiguration`
