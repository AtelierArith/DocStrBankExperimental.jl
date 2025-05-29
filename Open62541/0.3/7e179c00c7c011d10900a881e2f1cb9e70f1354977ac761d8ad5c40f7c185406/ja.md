```julia
struct UA_NetworkGroupDataType
```

フィールド:

  * `serverUri::Open62541.UA_String`
  * `networkPathsSize::UInt64`
  * `networkPaths::Ptr{Open62541.UA_EndpointUrlListDataType}`
