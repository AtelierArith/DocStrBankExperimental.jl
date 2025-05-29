```
JUA_ReferenceTypeAttributes
```

A mutable struct that defines a `JUA_ReferenceTypeAttributes` object - the equivalent of a `UA_ReferenceTypeAttributes`, but with memory managed by Julia rather than C (see below for exceptions)

The following constructor methods are defined:

```
JUA_ReferenceTypeAttributes(; kwargs...)
```

For valid keyword arguments `kwargs` see [`UA_ReferenceTypeAttributes_generate`](@ref).

```
JUA_ReferenceTypeAttributes(ptr::Ptr{UA_ReferenceTypeAttributes})
```

creates a `JUA_ReferenceTypeAttributes` based on the pointer `ptr`. This is a fallback method that can be used to pass `UA_ReferenceTypeAttributes`s generated via the low level interface to the higher level functions. See also [`UA_ReferenceTypeAttributes_generate`](@ref).

Note that memory management remains on the C side when using this method, i.e., `ptr` needs to be manually cleaned up with `UA_ReferenceTypeAttributes_delete(ptr)`  after the object is not needed anymore. It is up to the user to ensure this.
