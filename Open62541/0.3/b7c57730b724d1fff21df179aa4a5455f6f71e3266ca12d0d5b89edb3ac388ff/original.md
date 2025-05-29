```julia
struct UA_AddPublishedDataSetResult
```

Fields:

  * `addResult::UInt32`
  * `fieldAddResultsSize::UInt64`
  * `fieldAddResults::Ptr{UInt32}`
  * `configurationVersion::Open62541.UA_ConfigurationVersionDataType`
