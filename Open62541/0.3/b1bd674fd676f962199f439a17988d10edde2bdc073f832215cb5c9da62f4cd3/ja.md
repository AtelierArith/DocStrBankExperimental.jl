```
UA_ServerCallback_generate(f::Function)
```

は `UA_ServerCallback` オブジェクトを作成します。

`f` は次のシグネチャを持つJulia関数でなければなりません: `f(server::Ptr{UA_Server}, data::Ptr{Cvoid}))::Nothing`
