```julia
struct UA_SecurityPolicySignatureAlgorithm
```

フィールド:

  * `uri::Open62541.UA_String`
  * `verify::Ptr{Nothing}`
  * `sign::Ptr{Nothing}`
  * `getLocalSignatureSize::Ptr{Nothing}`
  * `getRemoteSignatureSize::Ptr{Nothing}`
  * `getLocalKeyLength::Ptr{Nothing}`
  * `getRemoteKeyLength::Ptr{Nothing}`
