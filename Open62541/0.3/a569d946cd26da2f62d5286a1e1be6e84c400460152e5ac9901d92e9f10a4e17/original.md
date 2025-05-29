```julia
struct UA_SessionlessInvokeResponseType
```

Fields:

  * `namespaceUrisSize::UInt64`
  * `namespaceUris::Ptr{Open62541.UA_String}`
  * `serverUrisSize::UInt64`
  * `serverUris::Ptr{Open62541.UA_String}`
  * `serviceId::UInt32`
