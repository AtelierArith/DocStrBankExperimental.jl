```
UA_Client_addObjectNode_async(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, typedefinition::Ptr{UA_NodeId},
        attr::Ptr{Open62541.UA_ObjectAttributes}, outNewNodeId::Ptr{UA_NodeId},
        callback::UA_ClientAsyncAddNodesCallback, userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

は、非同期クライアントAPIを使用して、`client`にオブジェクトノードを追加します。

有効な属性を定義する方法については、[`Open62541.UA_ObjectAttributes_generate`](@ref)を参照してください。
