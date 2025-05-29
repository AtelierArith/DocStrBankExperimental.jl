```julia
struct UA_CreateMonitoredItemsResponse
```

フィールド:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `resultsSize::UInt64`
  * `results::Ptr{Open62541.UA_MonitoredItemCreateResult}`
  * `diagnosticInfosSize::UInt64`
  * `diagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
