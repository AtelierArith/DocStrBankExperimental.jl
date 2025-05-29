```
UA_Client_addViewNode(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, attr::Ptr{Open62541.UA_ViewAttributes}, 
        outNewNodeId::Ptr{UA_NodeId})::UA_StatusCode
```

uses the client API to add a view  node to the `client`.

See [`Open62541.UA_ViewAttributes_generate`](@ref) on how to define valid  attributes.
