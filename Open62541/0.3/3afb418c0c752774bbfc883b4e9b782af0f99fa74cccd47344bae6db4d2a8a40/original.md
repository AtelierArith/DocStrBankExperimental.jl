```
JUA_MethodAttributes
```

A mutable struct that defines a `JUA_MethodAttributes` object - the equivalent of a `UA_MethodAttributes`, but with memory managed by Julia rather than C (see below for exceptions)

The following constructor methods are defined:

```
JUA_MethodAttributes(; kwargs...)
```

For valid keyword arguments `kwargs` see [`UA_MethodAttributes_generate`](@ref).

```
JUA_MethodAttributes(ptr::Ptr{UA_MethodAttributes})
```

creates a `JUA_MethodAttributes` based on the pointer `ptr`. This is a fallback method that can be used to pass `UA_MethodAttributes`s generated via the low level interface to the higher level functions. See also [`UA_MethodAttributes_generate`](@ref).

Note that memory management remains on the C side when using this method, i.e., `ptr` needs to be manually cleaned up with `UA_MethodAttributes_delete(ptr)` after the object is not needed anymore. It is up to the user to ensure this.
