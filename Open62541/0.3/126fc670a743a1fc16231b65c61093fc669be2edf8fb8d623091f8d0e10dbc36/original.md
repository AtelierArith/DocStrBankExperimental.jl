```julia
struct UA_DelayedCallback
```

Fields:

  * `next::Ptr{Open62541.UA_DelayedCallback}`
  * `callback::Ptr{Nothing}`
  * `application::Ptr{Nothing}`
  * `context::Ptr{Nothing}`
