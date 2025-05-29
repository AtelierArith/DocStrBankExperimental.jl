```
UA_MethodCallback_generate(f::Function)
```

creates a `UA_MethodCallback` that can be attached to a method node using `UA_Server_addMethodNode`.

`f` must be a Julia function with the following signature:

```
f(server::Ptr{UA_Server}, sessionId::Ptr{UA_NodeId}), sessionContext::Ptr{Cvoid}`, 
    methodId::Ptr{UA_NodeId}, methodContext::Ptr{Cvoid}, objectId::Ptr{UA_NodeId},   
    objectContext::Ptr{Cvoid}, inputSize::Csize_t, input::Ptr{UA_Variant},   
    outputSize::Csize_t, output::Ptr{UA_Variant})::UA_StatusCode
```

If the output of `f` only depends on the inputs, but not on any session state variables,  consider using [`UA_MethodCallback_wrap`](@ref).
