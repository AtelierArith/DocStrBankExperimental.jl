```
UA_Client_addReferenceTypeNode(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, attr::Ptr{Open62541.UA_ReferenceTypeAttributes}, 
        outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

は、`client`に参照タイプノードを追加するためにクライアントAPIを使用します。

有効な属性を定義する方法については、[`Open62541.UA_ReferenceTypeAttributes_generate`](@ref)を参照してください。
