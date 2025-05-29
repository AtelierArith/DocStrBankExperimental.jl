```julia
struct UA_GetEndpointsResponse
```

フィールド:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `endpointsSize::UInt64`
  * `endpoints::Ptr{Open62541.UA_EndpointDescription}`
