```julia
struct UA_VariableTypeAttributes
```

フィールド:

  * `specifiedAttributes::UInt32`
  * `displayName::Open62541.UA_LocalizedText`
  * `description::Open62541.UA_LocalizedText`
  * `writeMask::UInt32`
  * `userWriteMask::UInt32`
  * `value::Open62541.UA_Variant`
  * `dataType::Open62541.UA_NodeId`
  * `valueRank::Int32`
  * `arrayDimensionsSize::UInt64`
  * `arrayDimensions::Ptr{UInt32}`
  * `isAbstract::Bool`
