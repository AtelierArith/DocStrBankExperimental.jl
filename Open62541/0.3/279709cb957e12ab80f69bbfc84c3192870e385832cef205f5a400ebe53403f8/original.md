```julia
struct UA_EncodeJsonOptions
```

Fields:

  * `namespaces::Ptr{Open62541.UA_String}`
  * `namespacesSize::UInt64`
  * `serverUris::Ptr{Open62541.UA_String}`
  * `serverUrisSize::UInt64`
  * `useReversible::Bool`
  * `prettyPrint::Bool`
  * `unquotedKeys::Bool`
  * `stringNodeIds::Bool`
