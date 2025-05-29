```
JUA_Server_addNode(server::JUA_Server, requestedNewNodeId::JUA_NodeId,
        parentNodeId::JUA_NodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName, 
        attributes::Union{JUA_VariableAttributes, JUA_VariableTypeAttributes, JUA_ObjectAttributes},
        outNewNodeId::JUA_NodeId, nodeContext::JUA_NodeId, typeDefinition::JUA_NodeId)::UA_StatusCode
```

は、`server` に変数、変数型、またはオブジェクトノードを追加するためにサーバーAPIを使用します。

有効な属性を定義する方法については、[`JUA_VariableAttributes`](@ref)、[`JUA_VariableTypeAttributes`](@ref)、および [`JUA_ObjectAttributes`](@ref) を参照してください。

```
JUA_Server_addNode(server::JUA_Server, requestedNewNodeId::JUA_NodeId,
        parentNodeId::JUA_NodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName,
        attributes::Union{JUA_ObjectTypeAttributes, JUA_ReferenceTypeAttributes, JUA_DataTypeAttributes, JUA_ViewAttributes},
        outNewNodeId::JUA_NodeId, nodeContext::JUA_NodeId)::UA_StatusCode
```

は、`server` にオブジェクト型、参照型、データ型、またはビューのノードを追加するためにサーバーAPIを使用します。

有効な属性を定義する方法については、[`JUA_ObjectTypeAttributes`](@ref)、[`JUA_ReferenceTypeAttributes`](@ref)、[`JUA_DataTypeAttributes`](@ref)、および [`JUA_ViewAttributes`](@ref) を参照してください。

```
JUA_Server_addNode(server::JUA_Server, requestedNewNodeId::JUA_NodeId,
        parentNodeId::JUA_NodeId, referenceTypeId::JUA_NodeId, browseName::JUA_QualifiedName,
        attributes::JUA_MethodAttributes, method::Union{Function, Ptr{Cvoid}, Base.CFunction},
        inputArguments::Union{AbstractArray{JUA_Argument}, JUA_Argument}, 
        outputArguments::Union{AbstractArray{JUA_Argument}, JUA_Argument}, 
        outNewNodeId::JUA_NodeId, nodeContext::JUA_NodeId)::UA_StatusCode
```

は、`server` にメソッドノードを追加するためにサーバーAPIを使用します。

提供された `method` は、`UA_MethodCallback_wrap` または `UA_MethodCallback_generate` の要件を満たすJulia関数である必要があります。

また、以下も参照してください：

  * 有効な属性を定義する方法については、[`JUA_MethodAttributes`](@ref) を参照してください。
  * `method` の要件については、[`JUA_MethodCallback_generate`](@ref) を参照してください。
  * `method` の要件については、[`JUA_MethodCallback_wrap`](@ref) を参照してください。
