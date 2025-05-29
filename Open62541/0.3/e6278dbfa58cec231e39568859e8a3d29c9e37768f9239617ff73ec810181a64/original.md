```
UA_ClientAsyncReadCallback_generate(f::Function)
```

creates a `UA_ClientAsyncReadCallback` object.

`f` must be a Julia function with the following signature: `f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestId::UInt32, readresponse::Ptr{UA_ReadResponse}))::Nothing`
