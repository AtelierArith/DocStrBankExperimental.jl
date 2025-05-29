```
JUA_Client_addNode(client::JUA_Client, requestedNewNodeId::JUA_NodeId,
        parentNodeId::JUA_NodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName, 
        attributes::Union{JUA_VariableAttributes, JUA_ObjectAttributes},
        outNewNodeId::JUA_NodeId, typeDefinition::JUA_NodeId)::UA_StatusCode
```

は、クライアントが接続されているサーバーに変数またはオブジェクトノードを追加するためにクライアントAPIを使用します。

有効な属性を定義する方法については、[`JUA_VariableAttributes`](@ref)、[`JUA_VariableTypeAttributes`](@ref)、および[`JUA_ObjectAttributes`](@ref)を参照してください。

```
JUA_Client_addNode(client::JUA_Client, requestedNewNodeId::JUA_NodeId,
        parentNodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName,
        attributes::Union{JUA_VariableTypeAttributes, JUA_ObjectTypeAttributes, 
        JUA_ReferenceTypeAttributes, JUA_DataTypeAttributes, JUA_ViewAttributes},
        outNewNodeId::JUA_NodeId)::UA_StatusCode
```

は、クライアントが接続されているサーバーにオブジェクトタイプ、参照タイプ、データタイプ、またはビューノードを追加するためにクライアントAPIを使用します。

有効な属性を定義する方法については、[`JUA_VariableTypeAttributes](@ref)、[`JUA_ObjectTypeAttributes`](@ref)、[`JUA_ReferenceTypeAttributes`](@ref)、[`JUA_DataTypeAttributes`](@ref)、および[`JUA_ViewAttributes`](@ref)を参照してください。
