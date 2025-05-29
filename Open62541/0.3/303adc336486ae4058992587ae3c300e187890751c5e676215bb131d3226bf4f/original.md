```
UA_NODEID(s::AbstractString)::Ptr{UA_NodeId}
UA_NODEID(s::Ptr{UA_String})::Ptr{UA_NodeId}
```

creates a `UA_NodeId` object by parsing `s`.

Example:

```
UA_NODEID("ns=1;i=1234") #generates UA_NodeId with numeric identifier
UA_NODEID("ns=1;s=test") #generates UA_NodeId with string identifier
```
