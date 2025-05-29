```
JUA_Client_addNode_async(client::JUA_Client, requestedNewNodeId::JUA_NodeId,
        parentNodeId::JUA_NodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName, 
        attributes::Union{JUA_VariableAttributes, JUA_ObjectAttributes},
        outNewNodeId::JUA_NodeId, callback::UA_ClientAsyncAddNodesCallback, 
        userdata::Ptr{Cvoid}, requestId::UInt32, typeDefinition::JUA_NodeId)::UA_StatusCode
```

は、クライアントが接続されているサーバーに変数またはオブジェクトノードを追加するための**非同期**クライアントAPIを使用します。

有効な属性を定義する方法については、[`JUA_VariableAttributes`](@ref)または[`JUA_ObjectAttributes`](@ref)を参照してください。

```
JUA_Client_addNode_async(client::JUA_Client, requestedNewNodeId::JUA_NodeId,
        parentNodeId::JUA_NodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName, 
        attributes::Union{JUA_VariableTypeAttributes, JUA_ObjectTypeAttributes, 
        JUA_ViewAttributes, JUA_ReferenceTypeAttributes, JUA_DataTypeAttributes},
        outNewNodeId::JUA_NodeId, callback::UA_ClientAsyncAddNodesCallback, 
        userdata::Ptr{Cvoid}, requestId::UInt32, typeDefinition::JUA_NodeId)::UA_StatusCode
```

は、クライアントが接続されているサーバーにVariableType、ObjectType、ReferenceType、DataType、またはViewノードを追加するための**非同期**クライアントAPIを使用します。

有効な属性を定義する方法については、[`JUA_VariableTypeAttributes`](@ref)、[`JUA_ObjectTypeAttributes`](@ref)、[`JUA_ReferenceTypeAttributes`](@ref)、[`JUA_DataTypeAttributes`](@ref)、および[`JUA_ViewAttributes`](@ref)を参照してください。
