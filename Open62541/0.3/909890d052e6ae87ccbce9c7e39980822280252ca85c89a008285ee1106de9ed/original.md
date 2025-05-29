```
UA_ClientAsyncCallCallback_generate(f::Function)
```

creates a `UA_ClientAsyncCallCallback` object.

`f` must be a Julia function with the following signature: `f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestId::UInt32, callresponse::Ptr{UA_CallResponse}))::Nothing`
