```julia
struct UA_DecodeJsonOptions
```

Fields:

  * `namespaces::Ptr{Open62541.UA_String}`
  * `namespacesSize::UInt64`
  * `serverUris::Ptr{Open62541.UA_String}`
  * `serverUrisSize::UInt64`
  * `customTypes::Ptr{Open62541.UA_DataTypeArray}`
