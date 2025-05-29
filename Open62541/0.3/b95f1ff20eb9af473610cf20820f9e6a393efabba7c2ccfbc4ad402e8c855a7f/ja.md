```julia
struct UA_UadpDataSetReaderMessageDataType
```

フィールド:

  * `groupVersion::UInt32`
  * `networkMessageNumber::UInt16`
  * `dataSetOffset::UInt16`
  * `dataSetClassId::Open62541.UA_Guid`
  * `networkMessageContentMask::UInt32`
  * `dataSetMessageContentMask::UInt32`
  * `publishingInterval::Float64`
  * `receiveOffset::Float64`
  * `processingOffset::Float64`
