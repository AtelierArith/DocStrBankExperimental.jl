```
UA_ClientCallback_generate(f::Function)
```

は `UA_ClientCallback` オブジェクトを作成します。

`f` は次のシグネチャを持つJulia関数でなければなりません: `f(client::Ptr{UA_Client}, data::Ptr{Cvoid}))::Nothing`
