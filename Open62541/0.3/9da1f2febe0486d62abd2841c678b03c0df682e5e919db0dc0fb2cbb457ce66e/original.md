```
JUA_String
```

a mutable struct that defines a string type usable with open62541. It is the equivalent of a `UA_String`, but with memory managed by Julia rather than C.

The following constructor methods are defined:

```
JUA_String()
```

creates an empty `JUA_String`, equivalent to calling `UA_String_new()`.

```
JUA_String(s::AbstractString)
```

creates a `JUA_String` containing the string `s`.

```
JUA_String(ptr::Ptr{UA_String})
```

creates a `JUA_String` based on the pointer `ptr`. This is a fallback method that can be used to pass `UA_Guid`s generated via the low level interface to the higher level functions. Note that memory management remains on the C side when using this method, i.e., `ptr` needs to be manually cleaned up with `UA_String_delete(ptr)` after the object is not needed anymore. It is up to the user to ensure this.
