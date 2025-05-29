```
UA_ClientAsyncAddNodesCallback_generate(f::Function)
```

creates a `UA_ClientAsyncAddNodesCallback` object.

`f` must be a Julia function with the following signature: `f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestId::UInt32, writeresponse::Ptr{UA_AddNodesResponse}))::Nothing`
