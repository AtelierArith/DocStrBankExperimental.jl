```julia
struct UA_PubSubConfigurationDataType
```

フィールド:

  * `publishedDataSetsSize::UInt64`
  * `publishedDataSets::Ptr{Open62541.UA_PublishedDataSetDataType}`
  * `connectionsSize::UInt64`
  * `connections::Ptr{Open62541.UA_PubSubConnectionDataType}`
  * `enabled::Bool`
