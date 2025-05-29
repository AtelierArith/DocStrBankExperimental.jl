```julia
struct UA_GetEndpointsResponse
```

Fields:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `endpointsSize::UInt64`
  * `endpoints::Ptr{Open62541.UA_EndpointDescription}`
