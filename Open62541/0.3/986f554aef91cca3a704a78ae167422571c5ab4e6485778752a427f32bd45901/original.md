```julia
struct UA_HistoryModifiedData
```

Fields:

  * `dataValuesSize::UInt64`
  * `dataValues::Ptr{Open62541.UA_DataValue}`
  * `modificationInfosSize::UInt64`
  * `modificationInfos::Ptr{Open62541.UA_ModificationInfo}`
