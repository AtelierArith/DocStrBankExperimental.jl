```
UA_EXPANDEDNODEID(s::AbstractString)::Ptr{UA_ExpandedNodeId}
UA_EXPANDEDNODEID(s::Ptr{UA_String})::Ptr{UA_ExpandedNodeId}
```

creates a `UA_ExpandedNodeId` object by parsing `s`. Memory is allocated by C and needs to be cleaned up using `UA_ExpandedNodeId_delete(x::Ptr{UA_ExpandedNodeId})` after the object is not used anymore.

See also: [OPC Foundation Website](https://reference.opcfoundation.org/Core/Part6/v105/docs/5.2.2.10)

Example:

```
UA_EXPANDEDNODEID("svr=1;nsu=http://example.com;i=1234") #generates UA_ExpandedNodeId with numeric identifier
UA_EXPANDEDNODEID("svr=1;nsu=http://example.com;s=test") #generates UA_ExpandedNodeId with string identifier
```
