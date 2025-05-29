```julia
struct UA_TransferSubscriptionsResponse
```

フィールド:

  * `responseHeader::Open62541.UA_ResponseHeader`
  * `resultsSize::UInt64`
  * `results::Ptr{Open62541.UA_TransferResult}`
  * `diagnosticInfosSize::UInt64`
  * `diagnosticInfos::Ptr{Open62541.UA_DiagnosticInfo}`
