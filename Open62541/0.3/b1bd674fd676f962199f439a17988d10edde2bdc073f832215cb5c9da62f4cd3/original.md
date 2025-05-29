```
UA_ServerCallback_generate(f::Function)
```

creates a `UA_ServerCallback` object.

`f` must be a Julia function with the following signature: `f(server::Ptr{UA_Server}, data::Ptr{Cvoid}))::Nothing`
