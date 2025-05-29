```
UA_Client_addObjectNode_async(::Ptr{UA_Client}, requestednewnodeid::Ptr{UA_NodeId}, 
        parentnodeid::Ptr{UA_NodeId}, referenceTypeId::Ptr{UA_NodeId}, 
        browseName::Ptr{UA_QualifiedName}, typedefinition::Ptr{UA_NodeId},
        attr::Ptr{Open62541.UA_ObjectAttributes}, outNewNodeId::Ptr{UA_NodeId},
        callback::UA_ClientAsyncAddNodesCallback, userdata::Ptr{Cvoid}, requestId::UInt32)::UA_StatusCode
```

uses the asynchronous client API to add a object  node to the `client`.

See [`Open62541.UA_ObjectAttributes_generate`](@ref) on how to define valid  attributes.
