```
JUA_NodeId
```

creates a `JUA_ExpandedNodeId` object - the equivalent of a `UA_ExpandedNodeId`, but with memory managed by Julia rather than C.

See also: [OPC Foundation Website](https://reference.opcfoundation.org/Core/Part6/v105/docs/5.2.2.10)

The following methods are defined:

```
JUA_ExpandedNodeId()
```

creates a `JUA_ExpandedNodeId` with all fields equal to null.

```
JUA_ExpandedNodeId(s::Union{AbstractString, JUA_String, Ptr{UA_String}})
```

creates a `JUA_ExpandedNodeId` based on String `s` that is parsed into the relevant properties.

```
JUA_ExpandedNodeId(nsIndex::Integer, identifier::Integer)
```

creates a `JUA_ExpandedNodeId` with namespace index `nsIndex`, numeric NodeId identifier `identifier`, serverIndex = 0 and empty nameSpaceUri.

```
JUA_ExpandedNodeId(nsIndex::Integer, identifier::Union{AbstractString, JUA_String, Ptr{UA_String}})
```

creates a `JUA_ExpandedNodeId` with namespace index `nsIndex`, string NodeId identifier `identifier`, serverIndex = 0 and empty nameSpaceUri.

```
JUA_ExpandedNodeId(nodeId::Union{Ptr{UA_NodeId}, JUA_NodeId})
```

creates a `JUA_ExpandedNodeId` with empty namespaceUri, serverIndex = 0 and the content of `nodeId` in the nodeId field.

```
JUA_ExpandedNodeId(identifier::Integer, ns_uri::AbstractString, server_ind::Integer) 
```

creates a `JUA_ExpandedNodeId` with namespace index `nsIndex` and global unique id identifier `identifier` for the Nodeid, as well as serverIndex = 0 and empty namespaceUri.

```
JUA_ExpandedNodeId(identifier::Union{Ptr{UA_String}, AbstractString, JUA_String}, ns_uri::AbstractString, server_ind::Integer) 
```

creates a `JUA_ExpandedNodeId` with a string `identifier` for the nodeid, namespacUri `ns_uri` and server index `server_ind`.

```
JUA_ExpandedNodeId(guid::Union{Ptr{UA_Guid}, JUA_Guid}, ns_uri::AbstractString, server_ind::Integer) 
```

creates a `JUA_ExpandedNodeId` with its nodeid having the global unique identifier `guid`, namespaceUri `ns_uri` and server index `server_ind`.

```
JUA_ExpandedNodeId(nodeid::Union{Ptr{UA_NodeId}, JUA_NodeId}, ns_uri::AbstractString, server_ind::Integer)
```

creates a `JUA_ExpandedNodeId` from the JUA*NodeId `nodeid`, namespaceUri `ns*uri`and server index`server_ind`.

```
JUA_ExpandedNodeId(nptr::Ptr{UA_ExpandedNodeId})
```

creates a `JUA_ExpandedNodeId` based on the pointer `nptr`. This is a fallback method that can be used to pass `UA_NodeId`s generated via the low level interface to the higher level functions. Note that memory management remains on the C side when using this method, i.e., `nptr` needs to be manually cleaned up with `UA_ExpandedNodeId_delete(nptr)` after the object is not needed anymore. It is up to the user to ensure this.

Examples:

```
j = JUA_ExpandedNodeId()
j = JUA_ExpandedNodeId("ns=1;i=1234")
j = JUA_ExpandedNodeId("ns=1;s=example")
j = JUA_ExpandedNodeId(1, 1234)
j = JUA_ExpandedNodeId(1, "example")
j = JUA_ExpandedNodeId(1, JUA_Guid("C496578A-0DFE-4B8F-870A-745238C6AEAE"))
```
