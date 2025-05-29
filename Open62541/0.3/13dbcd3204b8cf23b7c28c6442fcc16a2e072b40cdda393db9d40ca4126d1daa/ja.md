```julia
struct UA_CreateSessionRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `clientDescription::Open62541.UA_ApplicationDescription`
  * `serverUri::Open62541.UA_String`
  * `endpointUrl::Open62541.UA_String`
  * `sessionName::Open62541.UA_String`
  * `clientNonce::Open62541.UA_String`
  * `clientCertificate::Open62541.UA_String`
  * `requestedSessionTimeout::Float64`
  * `maxResponseMessageSize::UInt32`
