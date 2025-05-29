```
JUA_QualifiedName
```

A mutable struct that defines a qualified name comprised of a namespace index and a text portion (a name). It is the equivalent of a `UA_QualifiedName`, but with memory managed by Julia rather than C.

The following constructor methods are defined:

```
JUA_QualifiedName()
```

creates an empty `JUA_QualifiedName`, equivalent to calling `UA_QualifiedName_new()`.

```
JUA_QualifiedName(nsIndex::Integer, identifier::AbstractString)
```

creates a `JUA_QualifiedName` with namespace index `nsIndex` and text identifier `identifier`.

```
JUA_QualifiedName(ptr::Ptr{UA_QualifiedName})
```

creates a `JUA_QualifiedName` based on the pointer `ptr`. This is a fallback method that can be used to pass `UA_QualifiedName`s generated via the low level interface to the higher level functions. Note that memory management remains on the C side when using this method, i.e., `ptr` needs to be manually cleaned up with `UA_QualifiedName_delete(ptr)` after the object is not needed anymore. It is up to the user to ensure this.
