```julia
struct UA_GenericAttributes
```

Fields:

  * `specifiedAttributes::UInt32`
  * `displayName::Open62541.UA_LocalizedText`
  * `description::Open62541.UA_LocalizedText`
  * `writeMask::UInt32`
  * `userWriteMask::UInt32`
  * `attributeValuesSize::UInt64`
  * `attributeValues::Ptr{Open62541.UA_GenericAttributeValue}`
