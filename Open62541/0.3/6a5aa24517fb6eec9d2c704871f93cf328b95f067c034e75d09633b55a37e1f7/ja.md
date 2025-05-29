```
UA_Server_addReferenceTypeNode(server::Ptr{UA_Server}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, typedefinition::Ptr{UA_NodeId},
        attr::Ptr{Open62541.UA_ReferenceTypeAttributes}, nodeContext::Ptr{UA_NodeId}, 
        outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

は、`server`に参照タイプノードを追加するためにサーバーAPIを使用します。

有効な属性を定義する方法については、[`Open62541.UA_ReferenceTypeAttributes_generate`](@ref)を参照してください。
