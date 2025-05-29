```julia
struct UA_QueryNextResponse
```

Fields:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `queryDataSetsSize::UInt64`
  * `queryDataSets::Ptr{Open62541.UA_QueryDataSet}`
  * `revisedContinuationPoint::Open62541.UA_String`
