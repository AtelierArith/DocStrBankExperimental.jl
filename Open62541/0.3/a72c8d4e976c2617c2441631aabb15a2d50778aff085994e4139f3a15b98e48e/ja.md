```
UA_Client_addDataTypeNode(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, attr::Ptr{Open62541.UA_DataTypeAttributes}, 
        outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

は、クライアントAPIを使用して、`client`にデータ型ノードを追加します。

有効な属性を定義する方法については、[`Open62541.UA_DataTypeAttributes_generate`](@ref)を参照してください。
