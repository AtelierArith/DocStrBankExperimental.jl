```
JUA_ObjectTypeAttributes
```

A mutable struct that defines a `JUA_ObjectTypeAttributes` object - the equivalent of a `UA_ObjectTypeAttributes`, but with memory managed by Julia rather than C (see below for exceptions).

The following constructor methods are defined:

```
JUA_ObjectTypeAttributes(; kwargs...)
```

For valid keyword arguments `kwargs` see [`UA_ObjectTypeAttributes_generate`](@ref).

```
JUA_ObjectTypeAttributes(ptr::Ptr{UA_ObjectTypeAttributes})
```

creates a `JUA_ObjectTypeAttributes` based on the pointer `ptr`. This is a fallback method that can be used to pass `UA_ObjectTypeAttributes`s generated via the low level interface to the higher level functions. See also [`UA_ObjectTypeAttributes_generate`](@ref).

Note that memory management remains on the C side when using this method, i.e., `ptr` needs to be manually cleaned up with `UA_ObjectTypeAttributes_delete(ptr)` after the object is not needed anymore. It is up to the user to ensure this.
