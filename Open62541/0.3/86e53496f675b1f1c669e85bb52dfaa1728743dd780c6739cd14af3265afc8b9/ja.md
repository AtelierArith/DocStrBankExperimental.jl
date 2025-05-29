```julia
struct UA_ResponseHeader
```

フィールド:

  * `timestamp::Int64`
  * `requestHandle::UInt32`
  * `serviceResult::UInt32`
  * `serviceDiagnostics::Open62541.UA_DiagnosticInfo`
  * `stringTableSize::UInt64`
  * `stringTable::Ptr{Open62541.UA_String}`
  * `additionalHeader::Open62541.UA_ExtensionObject`
