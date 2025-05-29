```julia
struct UA_SecurityPolicyEncryptionAlgorithm
```

フィールド:

  * `uri::Open62541.UA_String`
  * `encrypt::Ptr{Nothing}`
  * `decrypt::Ptr{Nothing}`
  * `getLocalKeyLength::Ptr{Nothing}`
  * `getRemoteKeyLength::Ptr{Nothing}`
  * `getRemoteBlockSize::Ptr{Nothing}`
  * `getRemotePlainTextBlockSize::Ptr{Nothing}`
