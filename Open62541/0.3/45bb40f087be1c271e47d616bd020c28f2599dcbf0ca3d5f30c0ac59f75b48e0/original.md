```julia
struct UA_CreateSessionResponse
```

Fields:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `sessionId::Open62541.UA_NodeId`
  * `authenticationToken::Open62541.UA_NodeId`
  * `revisedSessionTimeout::Float64`
  * `serverNonce::Open62541.UA_String`
  * `serverCertificate::Open62541.UA_String`
  * `serverEndpointsSize::UInt64`
  * `serverEndpoints::Ptr{Open62541.UA_EndpointDescription}`
  * `serverSoftwareCertificatesSize::UInt64`
  * `serverSoftwareCertificates::Ptr{Open62541.UA_SignedSoftwareCertificate}`
  * `serverSignature::Open62541.UA_SignatureData`
  * `maxRequestMessageSize::UInt32`
