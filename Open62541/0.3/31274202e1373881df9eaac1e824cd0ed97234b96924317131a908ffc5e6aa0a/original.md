```julia
struct UA_HistoryDataBackend
```

Fields:

  * `context::Ptr{Nothing}`
  * `deleteMembers::Ptr{Nothing}`
  * `serverSetHistoryData::Ptr{Nothing}`
  * `getHistoryData::Ptr{Nothing}`
  * `getDateTimeMatch::Ptr{Nothing}`
  * `getEnd::Ptr{Nothing}`
  * `lastIndex::Ptr{Nothing}`
  * `firstIndex::Ptr{Nothing}`
  * `resultSize::Ptr{Nothing}`
  * `copyDataValues::Ptr{Nothing}`
  * `getDataValue::Ptr{Nothing}`
  * `boundSupported::Ptr{Nothing}`
  * `timestampsToReturnSupported::Ptr{Nothing}`
  * `insertDataValue::Ptr{Nothing}`
  * `replaceDataValue::Ptr{Nothing}`
  * `updateDataValue::Ptr{Nothing}`
  * `removeDataValue::Ptr{Nothing}`
