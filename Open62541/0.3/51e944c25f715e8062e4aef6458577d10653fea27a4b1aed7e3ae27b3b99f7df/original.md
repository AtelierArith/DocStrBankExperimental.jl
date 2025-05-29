```julia
struct UA_MethodAttributes
```

Fields:

  * `specifiedAttributes::UInt32`
  * `displayName::Open62541.UA_LocalizedText`
  * `description::Open62541.UA_LocalizedText`
  * `writeMask::UInt32`
  * `userWriteMask::UInt32`
  * `executable::Bool`
  * `userExecutable::Bool`
