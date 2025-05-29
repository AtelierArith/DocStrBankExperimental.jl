```julia
struct UA_CertificateVerification
```

Fields:

  * `context::Ptr{Nothing}`
  * `verifyCertificate::Ptr{Nothing}`
  * `verifyApplicationURI::Ptr{Nothing}`
  * `getExpirationDate::Ptr{Nothing}`
  * `getSubjectName::Ptr{Nothing}`
  * `clear::Ptr{Nothing}`
  * `logging::Ptr{Open62541.UA_Logger}`
