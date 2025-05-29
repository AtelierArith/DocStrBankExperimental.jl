```
JUA_ObjectAttributes
```

A mutable struct that defines a `JUA_ObjectAttributes` object - the equivalent of a `UA_ObjectAttributes`, but with memory managed by Julia rather than C (see below for exceptions)

The following constructor methods are defined:

```
JUA_ObjectAttributes(; kwargs...)
```

For valid keyword arguments `kwargs` see [`UA_ObjectAttributes_generate`](@ref).

```
JUA_ObjectAttributes(ptr::Ptr{UA_ObjectAttributes})
```

creates a `JUA_ObjectAttributes` based on the pointer `ptr`. This is a fallback method that can be used to pass `UA_ObjectAttributes`s generated via the low level interface to the higher level functions. See also [`UA_ObjectAttributes_generate`](@ref).

Note that memory management remains on the C side when using this method, i.e., `ptr` needs to be manually cleaned up with `UA_ObjectAttributes_delete(ptr)` after the object is not needed anymore. It is up to the user to ensure this.
