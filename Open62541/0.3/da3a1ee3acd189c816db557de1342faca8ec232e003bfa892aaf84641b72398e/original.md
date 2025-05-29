```
JUA_NodeId
```

creates a `JUA_NodeId` object - the equivalent of a `UA_NodeId`, but with memory managed by Julia rather than C.

The following methods are defined:

```
JUA_NodeId()
```

creates a `JUA_NodeId` with namespaceIndex = 0, numeric identifierType and identifier = 0

```
JUA_NodeId(s::AbstractString)
```

creates a `JUA_NodeId` based on String `s` that is parsed into the relevant properties.

```
JUA_NodeId(nsIndex::Integer, identifier::Integer)
```

creates a `JUA_NodeId` with namespace index `nsIndex` and numerical identifier `identifier`.

```
JUA_NodeId(nsIndex::Integer, identifier::AbstractString)
```

creates a `JUA_NodeId` with namespace index `nsIndex` and string identifier `identifier`.

```
JUA_NodeId(nsIndex::Integer, identifier::JUA_Guid)
```

creates a `JUA_NodeId` with namespace index `nsIndex` and global unique id identifier `identifier`.

```
JUA_NodeId(nptr::Ptr{UA_NodeId})
```

creates a `JUA_NodeId` based on the pointer `nptr`. This is a fallback method that can be used to pass `UA_NodeId`s generated via the low level interface to the higher level functions. Note that memory management remains on the C side when using this method, i.e., `nptr` needs to be manually cleaned up with `UA_NodeId_delete(nptr)` after the object is not needed anymore. It is up to the user to ensure this.

Examples:

```
j = JUA_NodeId()
j = JUA_NodeId("ns=1;i=1234")
j = JUA_NodeId("ns=1;s=example")
j = JUA_NodeId(1, 1234)
j = JUA_NodeId(1, "example")
j = JUA_NodeId(1, JUA_Guid("C496578A-0DFE-4B8F-870A-745238C6AEAE"))
```
