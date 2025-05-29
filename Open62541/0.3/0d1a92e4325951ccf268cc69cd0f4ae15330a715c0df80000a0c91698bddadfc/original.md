```
UA_NodeTypeLifeCycleCallback_constructor_generate(f::Function)
```

creates a function pointer for the `constructor` field of a `UA_NodeTypeLifeCycle` object.

`f` must be a Julia function with the following signature:

```
f(server::Ptr{UA_Server}, sessionId:: Ptr{UA_NodeId},
       sessionContext::Ptr{Cvoid}, typeNodeId::Ptr{UA_NodeId}, typeNodeContext::Ptr{Cvoid}, 
       nodeId::Ptr{UA_NodeId}, nodeContext::Ptr{Ptr{Cvoid}})::UA_StatusCode
```
