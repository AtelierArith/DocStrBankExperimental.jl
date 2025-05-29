```julia
struct UA_ViewAttributes
```

フィールド:

  * `specifiedAttributes::UInt32`
  * `displayName::Open62541.UA_LocalizedText`
  * `description::Open62541.UA_LocalizedText`
  * `writeMask::UInt32`
  * `userWriteMask::UInt32`
  * `containsNoLoops::Bool`
  * `eventNotifier::UInt8`
