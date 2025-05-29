```julia
struct UA_QueryFirstResponse
```

Fields:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `queryDataSetsSize::UInt64`
  * `queryDataSets::Ptr{Open62541.UA_QueryDataSet}`
  * `continuationPoint::Open62541.UA_String`
  * `parsingResultsSize::UInt64`
  * `parsingResults::Ptr{Open62541.UA_ParsingResult}`
  * `diagnosticInfosSize::UInt64`
  * `diagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
  * `filterResult::Open62541.UA_ContentFilterResult`
