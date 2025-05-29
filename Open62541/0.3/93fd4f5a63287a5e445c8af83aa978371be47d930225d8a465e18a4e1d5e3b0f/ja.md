```
UA_EXPANDEDNODEID(s::AbstractString)::Ptr{UA_ExpandedNodeId}
UA_EXPANDEDNODEID(s::Ptr{UA_String})::Ptr{UA_ExpandedNodeId}
```

は、`s`を解析することによって`UA_ExpandedNodeId`オブジェクトを作成します。メモリはCによって割り当てられ、オブジェクトがもはや使用されない場合は`UA_ExpandedNodeId_delete(x::Ptr{UA_ExpandedNodeId})`を使用してクリーンアップする必要があります。

参照: [OPC Foundation Website](https://reference.opcfoundation.org/Core/Part6/v105/docs/5.2.2.10)

例:

```
UA_EXPANDEDNODEID("svr=1;nsu=http://example.com;i=1234") #数値識別子を持つUA_ExpandedNodeIdを生成
UA_EXPANDEDNODEID("svr=1;nsu=http://example.com;s=test") #文字列識別子を持つUA_ExpandedNodeIdを生成
```
