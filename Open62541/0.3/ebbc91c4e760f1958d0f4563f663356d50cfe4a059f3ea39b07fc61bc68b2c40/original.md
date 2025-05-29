```julia
struct UA_UadpWriterGroupMessageDataType
```

Fields:

  * `groupVersion::UInt32`
  * `dataSetOrdering::Open62541.UA_DataSetOrderingType`
  * `networkMessageContentMask::UInt32`
  * `samplingOffset::Float64`
  * `publishingOffsetSize::UInt64`
  * `publishingOffset::Ptr{Float64}`
