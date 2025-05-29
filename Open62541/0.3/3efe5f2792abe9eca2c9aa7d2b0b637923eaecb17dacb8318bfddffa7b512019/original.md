```
UA_Client_addVariableNode(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, typedefinition::Ptr{UA_NodeId},
        attr::Ptr{Open62541.UA_VariableAttributes}, outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

uses the client API to add a variable  node to the `client`.

See [`Open62541.UA_VariableAttributes_generate`](@ref) on how to define valid  attributes.
