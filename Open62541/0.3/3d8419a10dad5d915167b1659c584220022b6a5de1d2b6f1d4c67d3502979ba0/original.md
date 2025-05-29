```
UA_ClientAsyncServiceCallback_generate(f::Function)
```

creates a `UA_ClientAsyncServiceCallback` object.

`f` must be a Julia function with the following signature: `f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestId::UInt32, response::Ptr{Cvoid}))::Nothing`
