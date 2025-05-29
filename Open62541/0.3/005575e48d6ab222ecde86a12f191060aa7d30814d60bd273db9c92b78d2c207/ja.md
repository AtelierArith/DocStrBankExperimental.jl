```julia
struct UA_Argument
```

フィールド:

  * `name::Open62541.UA_String`
  * `dataType::Open62541.UA_NodeId`
  * `valueRank::Int32`
  * `arrayDimensionsSize::UInt64`
  * `arrayDimensions::Ptr{UInt32}`
  * `description::Open62541.UA_LocalizedText`
