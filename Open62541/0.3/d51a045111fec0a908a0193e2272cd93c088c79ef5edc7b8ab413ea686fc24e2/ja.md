```
UA_ClientAsyncReadValueAttributeCallback_generate(f::Function)
```

は、`UA_Client_readValueAttribute_async`にコールバック引数として供給できる`UA_ClientAsyncReadValueAttributeCallback`を生成します。コールバックは、読み取り操作が実行された後にトリガーされます。

`f`は、以下のシグネチャを持つJulia関数でなければなりません：

```
f(client::Ptr{UA_Client}, userdata::Ptr{Cvoid}, requestid::UA_UInt32, 
    status::UA_StatusCode, value)::UA_DataValue)::Nothing
```
