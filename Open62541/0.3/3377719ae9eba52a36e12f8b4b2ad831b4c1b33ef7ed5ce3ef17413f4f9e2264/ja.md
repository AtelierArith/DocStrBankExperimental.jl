```
UA_ValueCallback_onWrite_generate(f::Function)
```

は、`UA_ValueCallback`オブジェクトの`onWrite`フィールドのための関数ポインタを作成します。

`f`は、以下のシグネチャを持つJulia関数でなければなりません：

```
f(server::Ptr{UA_Server}, sessionid::Ptr{UA_NodeId}), sessioncontext::Ptr{Cvoid},
        nodeid::Ptr{Cvoid}, nodecontext::Ptr{Cvoid}, range::Ptr{UA_NumericRange}, 
        data::Ptr{UA_DataValue})::Nothing
```
