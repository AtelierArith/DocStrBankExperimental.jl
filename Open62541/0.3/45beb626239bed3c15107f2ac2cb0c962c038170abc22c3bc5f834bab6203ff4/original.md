```julia
struct UA_DeleteEventDetails
```

Fields:

  * `nodeId::Open62541.UA_NodeId`
  * `eventIdsSize::UInt64`
  * `eventIds::Ptr{Open62541.UA_String}`
