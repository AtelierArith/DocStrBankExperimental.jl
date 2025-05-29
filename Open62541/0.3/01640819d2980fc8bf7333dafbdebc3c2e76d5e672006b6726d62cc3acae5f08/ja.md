```julia
struct UA_TrustListDataType
```

フィールド:

  * `specifiedLists::UInt32`
  * `trustedCertificatesSize::UInt64`
  * `trustedCertificates::Ptr{Open62541.UA_String}`
  * `trustedCrlsSize::UInt64`
  * `trustedCrls::Ptr{Open62541.UA_String}`
  * `issuerCertificatesSize::UInt64`
  * `issuerCertificates::Ptr{Open62541.UA_String}`
  * `issuerCrlsSize::UInt64`
  * `issuerCrls::Ptr{Open62541.UA_String}`
