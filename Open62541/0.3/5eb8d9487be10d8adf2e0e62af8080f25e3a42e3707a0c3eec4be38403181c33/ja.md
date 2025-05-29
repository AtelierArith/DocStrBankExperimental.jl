```
UA_Client_addViewNode(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, attr::Ptr{Open62541.UA_ViewAttributes}, 
        outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

は、`client` にビュー ノードを追加するためにクライアント API を使用します。

有効な属性を定義する方法については、[`Open62541.UA_ViewAttributes_generate`](@ref) を参照してください。
