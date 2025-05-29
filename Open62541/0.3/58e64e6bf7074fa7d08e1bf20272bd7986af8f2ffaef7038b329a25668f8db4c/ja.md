```julia
struct UA_Variant
```

フィールド:

  * `type::Ptr{Open62541.UA_DataType}`
  * `storageType::Open62541.UA_VariantStorageType`
  * `arrayLength::UInt64`
  * `data::Ptr{Nothing}`
  * `arrayDimensionsSize::UInt64`
  * `arrayDimensions::Ptr{UInt32}`
