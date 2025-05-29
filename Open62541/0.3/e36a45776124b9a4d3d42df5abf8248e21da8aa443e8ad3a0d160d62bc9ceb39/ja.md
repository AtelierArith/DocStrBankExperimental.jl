```
UA_Server_addMethodNode(server::Ptr{UA_Server}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, attr::Ptr{UA_MethodAttributes}, 
        method::UA_MethodCallback, inputArgumentsSize::Csize_t, inputArguments::Union{UA_Argument, AbstractArray{UA_Argument}}, 
        outputArgumentsSize::Csize_t, outputArguments::Union{UA_Argument, AbstractArray{UA_Argument}}, 
        nodeContext::Ptr{UA_NodeId}, outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

は、コールバック `method` を持つメソッドノードを `server` に追加するためにサーバーAPIを使用します。

参照：

[`UA_MethodAttributes_generate`](@ref) 有効な属性を定義するため。

[`UA_MethodAttributes_generate`](@ref) 有効なコールバックを生成するため。
