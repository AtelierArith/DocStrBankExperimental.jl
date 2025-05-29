```
UA_ClientAsyncReadValueRankAttributeCallback_generate(f::Function)
```

は、`UA_Client_readValueRankAttribute_async`にコールバック引数として供給できる`UA_ClientAsyncReadValueRankAttributeCallback`を生成します。コールバックは、読み取り操作が実行された後にトリガーされます。

`f`は、次のシグネチャを持つJulia関数でなければなりません：

```
f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestid::UA_UInt32, 
    status::UA_StatusCode, valuerank)::UA_UInt32)::Nothing
```
