```
UA_Client_addObjectNode(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, typedefinition::Ptr{UA_NodeId},
        attr::Ptr{Open62541.UA_ObjectAttributes}, outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

は、`client`にオブジェクトノードを追加するためにクライアントAPIを使用します。

有効な属性を定義する方法については、[`Open62541.UA_ObjectAttributes_generate`](@ref)を参照してください。
