```julia
struct UA_CallMethodRequest
```

Fields:

  * `objectId::Open62541.UA_NodeId`
  * `methodId::Open62541.UA_NodeId`
  * `inputArgumentsSize::UInt64`
  * `inputArguments::Ptr{Open62541.UA_Variant}`
