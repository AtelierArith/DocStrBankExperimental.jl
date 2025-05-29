```
JUA_Guid
```

a mutable struct that defines a globally unique identifier. It is the equivalent of a `UA_Guid`, but with memory managed by Julia rather than C.

The following constructor methods are defined:

```
JUA_Guid()
```

creates an empty `JUA_Guid`, equivalent to calling `UA_Guid_new()`.

```
JUA_Guid(guidstring::AbstractString)
```

creates a `JUA_Guid` by parsing the string `guidstring`. The string should be formatted according to the OPC standard defined in Part 6, 5.1.3.

```
JUA_Guid(ptr::Ptr{UA_Guid})
```

creates a `JUA_Guid` based on the pointer `ptr`. This is a fallback method that can be used to pass `UA_Guid`s generated via the low level interface to the higher level functions. Note that memory management remains on the C side when using this method, i.e., `ptr` needs to be manually cleaned up with `UA_Guid_delete(ptr)` after the object is not needed anymore. It is up to the user to ensure this.
