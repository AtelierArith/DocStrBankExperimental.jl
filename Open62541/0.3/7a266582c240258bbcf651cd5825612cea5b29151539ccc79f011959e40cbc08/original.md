```
JUA_Server_addNode(server::JUA_Server, requestedNewNodeId::JUA_NodeId,
        parentNodeId::JUA_NodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName, 
        attributes::Union{JUA_VariableAttributes, JUA_VariableTypeAttributes, JUA_ObjectAttributes},
        outNewNodeId::JUA_NodeId, nodeContext::JUA_NodeId, typeDefinition::JUA_NodeId)::UA_StatusCode
```

uses the server API to add a Variable, VariableType, or Object node to the `server`.

See [`JUA_VariableAttributes`](@ref), [`JUA_VariableTypeAttributes`](@ref), and [`JUA_ObjectAttributes`](@ref) on how to define valid attributes.

```
JUA_Server_addNode(server::JUA_Server, requestedNewNodeId::JUA_NodeId,
        parentNodeId::JUA_NodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName,
        attributes::Union{JUA_ObjectTypeAttributes, JUA_ReferenceTypeAttributes, JUA_DataTypeAttributes, JUA_ViewAttributes},
        outNewNodeId::JUA_NodeId, nodeContext::JUA_NodeId)::UA_StatusCode
```

uses the server API to add a ObjectType, ReferenceType, DataType, or View node to the `server`.

See [`JUA_ObjectTypeAttributes`](@ref), [`JUA_ReferenceTypeAttributes`](@ref), [`JUA_DataTypeAttributes`](@ref), and [`JUA_ViewAttributes`](@ref) on how to define valid attributes.

```
JUA_Server_addNode(server::JUA_Server, requestedNewNodeId::JUA_NodeId,
        parentNodeId::JUA_NodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName,
        attributes::JUA_MethodAttributes, method::Union{Function, Ptr{Cvoid}, Base.CFunction},
        inputArguments::Union{AbstractArray{JUA_Argument}, JUA_Argument}, 
        outputArguments::Union{AbstractArray{JUA_Argument}, JUA_Argument}, 
        outNewNodeId::JUA_NodeId, nodeContext::JUA_NodeId)::UA_StatusCode
```

uses the server API to add a Method node to the `server`.

The `method` supplied can either be a Julia function that fulfills the requirements for  `UA_MethodCallback_wrap` or `UA_MethodCallback_generate`.

See also:

  * [`JUA_MethodAttributes`](@ref) for how to define valid attributes.
  * [`JUA_MethodCallback_generate`](@ref) for requirements on `method`.
  * [`JUA_MethodCallback_wrap`](@ref) for requirements on `method`.
