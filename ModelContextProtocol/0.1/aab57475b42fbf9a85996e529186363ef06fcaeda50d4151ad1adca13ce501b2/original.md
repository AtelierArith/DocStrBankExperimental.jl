```
JSONRPCNotification(; method::String, 
                   params::Union{RequestParams,Dict{String,Any}}) <: Notification
```

JSON-RPC notification message that does not expect a response.

# Fields

  * `method::String`: Name of the notification method
  * `params::Union{RequestParams,Dict{String,Any}}`: Parameters for the notification
