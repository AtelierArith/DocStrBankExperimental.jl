```
JUA_Client_addNode_async(client::JUA_Client, requestedNewNodeId::JUA_NodeId,
        parentNodeId::JUA_NodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName, 
        attributes::Union{JUA_VariableAttributes, JUA_ObjectAttributes},
        outNewNodeId::JUA_NodeId, callback::UA_ClientAsyncAddNodesCallback, 
        userdata::Ptr{Cvoid}, requestId::UInt32, typeDefinition::JUA_NodeId)::UA_StatusCode
```

uses the **asynchronous** client API to add a Variable or Object node to the server to which the client is connected to.

See [`JUA_VariableAttributes`](@ref) or [`JUA_ObjectAttributes`](@ref) on how to define valid attributes.

```
JUA_Client_addNode_async(client::JUA_Client, requestedNewNodeId::JUA_NodeId,
        parentNodeId::JUA_NodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName, 
        attributes::Union{JUA_VariableTypeAttributes, JUA_ObjectTypeAttributes, 
        JUA_ViewAttributes, JUA_ReferenceTypeAttributes, JUA_DataTypeAttributes},
        outNewNodeId::JUA_NodeId, callback::UA_ClientAsyncAddNodesCallback, 
        userdata::Ptr{Cvoid}, requestId::UInt32, typeDefinition::JUA_NodeId)::UA_StatusCode
```

uses the **asynchronous** client API to add a VariableType, ObjectType, ReferenceType, DataType or View node to the server to which the client is connected to.

See [`JUA_VariableTypeAttributes`](@ref), [`JUA_ObjectTypeAttributes`](@ref), [`JUA_ReferenceTypeAttributes`](@ref), [`JUA_DataTypeAttributes`](@ref), and [`JUA_ViewAttributes`](@ref) on how to define valid attributes.
