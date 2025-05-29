```
UA_Client_addReferenceTypeNode(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, attr::Ptr{Open62541.UA_ReferenceTypeAttributes}, 
        outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

uses the client API to add a referencetype  node to the `client`.

See [`Open62541.UA_ReferenceTypeAttributes_generate`](@ref) on how to define valid  attributes.
