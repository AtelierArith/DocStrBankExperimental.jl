```
JSONRPCRequest(; id::RequestId, method::String, 
             params::Union{RequestParams, Nothing}, 
             meta::RequestMeta=RequestMeta()) <: Request
```

JSON-RPC request message used to invoke methods on the server.

# Fields

  * `id::RequestId`: Unique identifier for the request
  * `method::String`: Name of the method to invoke
  * `params::Union{RequestParams, Nothing}`: Parameters for the method
  * `meta::RequestMeta`: Additional metadata for the request
