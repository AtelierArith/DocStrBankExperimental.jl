```
UA_DataSourceCallback_read_generate(f::Function)
```

は、`UA_DataSource`オブジェクトの`read`フィールドのための関数ポインタを作成します。

`f`は、以下のシグネチャを持つJulia関数でなければなりません：

```
f(server::Ptr{UA_Server}, sessionid::Ptr{UA_NodeId}), sessioncontext::Ptr{Cvoid},
        nodeid::Ptr{Cvoid}, nodecontext::Ptr{Cvoid}, includesourcetimestamp::UA_Boolean, 
        range::Ptr{UA_NumericRange}, data::Ptr{UA_DataValue})::UA_StatusCode
```
