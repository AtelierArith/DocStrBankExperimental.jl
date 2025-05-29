```
UA_ClientAsyncReadAccessLevelAttributeCallback_generate(f::Function)
```

は、`UA_Client_readAccessLevelAttribute_async`にコールバック引数として供給できる`UA_ClientAsyncReadAccessLevelAttributeCallback`を生成します。このコールバックは、読み取り操作が実行された後にトリガーされます。

`f`は、次のシグネチャを持つJulia関数でなければなりません：

```
f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestid::UA_UInt32, 
    status::UA_StatusCode, accesslevel)::UA_Byte::Nothing
```
