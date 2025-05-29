```julia
struct UA_PriorityMappingEntryType
```

Fields:

  * `mappingUri::Open62541.UA_String`
  * `priorityLabel::Open62541.UA_String`
  * `priorityValue_PCP::UInt8`
  * `priorityValue_DSCP::UInt32`
