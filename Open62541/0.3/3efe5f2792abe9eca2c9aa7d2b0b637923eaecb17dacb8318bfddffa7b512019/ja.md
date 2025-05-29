```
UA_Client_addVariableNode(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, typedefinition::Ptr{UA_NodeId},
        attr::Ptr{Open62541.UA_VariableAttributes}, outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

は、`client`に変数ノードを追加するためにクライアントAPIを使用します。

有効な属性を定義する方法については、[`Open62541.UA_VariableAttributes_generate`](@ref)を参照してください。
