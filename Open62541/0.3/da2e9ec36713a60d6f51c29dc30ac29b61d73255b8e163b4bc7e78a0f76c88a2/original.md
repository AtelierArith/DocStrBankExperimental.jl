```
UA_ClientCallback_generate(f::Function)
```

creates a `UA_ClientCallback` object.

`f` must be a Julia function with the following signature: `f(client::Ptr{UA_Client}, data::Ptr{Cvoid}))::Nothing`
