```
JUA_DataTypeAttributes
```

A mutable struct that defines a `JUA_DataTypeAttributes` object - the equivalent of a `UA_DataTypeAttributes`, but with memory managed by Julia rather than C (see below for exceptions)

The following constructor methods are defined:

```
JUA_DataTypeAttributes(; kwargs...)
```

For valid keyword arguments `kwargs` see [`UA_DataTypeAttributes_generate`](@ref).

```
JUA_DataTypeAttributes(ptr::Ptr{UA_DataTypeAttributes})
```

creates a `JUA_DataTypeAttributes` based on the pointer `ptr`. This is a fallback method that can be used to pass `UA_VariableAttributes`s generated via the low level interface to the higher level functions. See also [`UA_VariableAttributes_generate`](@ref).

Note that memory management remains on the C side when using this method, i.e., `ptr` needs to be manually cleaned up with `UA_DataTypeAttributes_delete(ptr)`  after the object is not needed anymore. It is up to the user to ensure this.
