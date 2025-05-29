```
UA_Client_addObjectNode(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, typedefinition::Ptr{UA_NodeId},
        attr::Ptr{Open62541.UA_ObjectAttributes}, outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

uses the client API to add a object  node to the `client`.

See [`Open62541.UA_ObjectAttributes_generate`](@ref) on how to define valid  attributes.
