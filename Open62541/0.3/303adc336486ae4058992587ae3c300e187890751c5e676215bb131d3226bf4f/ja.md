```
UA_NODEID(s::AbstractString)::Ptr{UA_NodeId}
UA_NODEID(s::Ptr{UA_String})::Ptr{UA_NodeId}
```

は `s` を解析することによって `UA_NodeId` オブジェクトを作成します。

例:

```
UA_NODEID("ns=1;i=1234") #数値識別子を持つ UA_NodeId を生成
UA_NODEID("ns=1;s=test") #文字列識別子を持つ UA_NodeId を生成
```
