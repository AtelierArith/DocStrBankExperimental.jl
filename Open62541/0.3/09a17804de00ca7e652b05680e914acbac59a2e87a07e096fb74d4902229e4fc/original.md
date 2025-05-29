```julia
struct UA_BrowsePathResult
```

Fields:

  * `statusCode::UInt32`
  * `targetsSize::UInt64`
  * `targets::Ptr{Open62541.UA_BrowsePathTarget}`
