```
UA_ClientReadArrayDimensionsAttributeCallback_generate(f::Function)
```

は、`UA_Client_readUA_ClientReadArrayDimensionsAttribute_async`にコールバック引数として供給できる`UA_ClientReadArrayDimensionsAttributeCallback`を作成します。コールバックは、読み取り操作が実行された後にトリガーされます。

`f`は、次のシグネチャを持つJulia関数でなければなりません：

```
f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestid::UA_UInt32, 
    status::UA_StatusCode, arraydimensions)::UA_Variant)::Nothing
```
