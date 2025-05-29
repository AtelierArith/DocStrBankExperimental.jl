```julia
struct UA_RequestHeader
```

Fields:

  * `authenticationToken::Open62541.UA_NodeId`
  * `timestamp::Int64`
  * `requestHandle::UInt32`
  * `returnDiagnostics::UInt32`
  * `auditEntryId::Open62541.UA_String`
  * `timeoutHint::UInt32`
  * `additionalHeader::Open62541.UA_ExtensionObject`
