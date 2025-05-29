```
UA_ClientAsyncReadWriteMaskAttributeCallback_generate(f::Function)
```

は、`UA_Client_readWriteMaskAttribute_async`にコールバック引数として供給できる`UA_ClientAsyncReadWriteMaskAttributeCallback`を生成します。このコールバックは、読み取り操作が実行された後にトリガーされます。

`f`は、以下のシグネチャを持つJulia関数でなければなりません：

```
f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestid::UA_UInt32, 
    status::UA_StatusCode, writeMask)::UA_UInt32)::Nothing
```
