```
UA_Server_addMethodNode(server::Ptr{UA_Server}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, attr::Ptr{UA_MethodAttributes}, 
        method::UA_MethodCallback, inputArgumentsSize::Csize_t, inputArguments::Union{UA_Argument, AbstractArray{UA_Argument}}, 
        outputArgumentsSize::Csize_t, outputArguments::Union{UA_Argument, AbstractArray{UA_Argument}}, 
        nodeContext::Ptr{UA_NodeId}, outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

uses the server API to add a method node with the callback `method` to the `server`.

See also:

[`UA_MethodAttributes_generate`](@ref) to define valid attributes.

[`UA_MethodAttributes_generate`](@ref) to generate a valid callback.
