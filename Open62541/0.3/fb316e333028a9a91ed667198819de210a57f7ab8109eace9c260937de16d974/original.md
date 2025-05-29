```
UA_Server_addDataTypeNode(server::Ptr{UA_Server}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, typedefinition::Ptr{UA_NodeId},
        attr::Ptr{Open62541.UA_DataTypeAttributes}, nodeContext::Ptr{UA_NodeId}, 
        outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

uses the server API to add a datatype node to the `server`.

See [`Open62541.UA_DataTypeAttributes_generate`](@ref) on how to define valid attributes.
