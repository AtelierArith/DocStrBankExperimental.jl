```julia
struct UA_ActivateSessionRequest
```

フィールド:

  * `requestHeader::Open62541.UA_RequestHeader`
  * `clientSignature::Open62541.UA_SignatureData`
  * `clientSoftwareCertificatesSize::UInt64`
  * `clientSoftwareCertificates::Ptr{Open62541.UA_SignedSoftwareCertificate}`
  * `localeIdsSize::UInt64`
  * `localeIds::Ptr{Open62541.UA_String}`
  * `userIdentityToken::Open62541.UA_ExtensionObject`
  * `userTokenSignature::Open62541.UA_SignatureData`
