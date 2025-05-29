```
UA_Client_addObjectTypeNode_async(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, attr::Ptr{Open62541.UA_ObjectTypeAttributes}, 
        outNewNodeId::Ptr{UA_NodeId}, callback::UA_ClientAsyncAddNodesCallback, 
        userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

は、非同期クライアントAPIを使用して、`client`にオブジェクトタイプノードを追加します。

有効な属性を定義する方法については、[`Open62541.UA_ObjectTypeAttributes_generate`](@ref)を参照してください。
