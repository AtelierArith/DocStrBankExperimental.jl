```
JUA_CallMethodRequest
```

A mutable struct that defines a `JUA_CallMethodRequest` object - the equivalent of a `UA_CallMethodRequest`, but with memory managed by Julia rather than C (exceptions below).

The following constructor methods are defined:

```
JUA_CallMethodRequest()
```

creates an empty `JUA_CallMethodRequest`, equivalent to calling `UA_CallMethodRequest_new()`.

```
JUA_CallMethodRequest(objectid::JUA_NodeId, methodid::JUA_NodeId, inputarg::Union{Any, Tuple{Any, ...}})
```

creates a `JUA_CallMethodRequest` taking the context nodeid (`objectid`), the nodeid of the method to be called (`methodid`)`, as well as the`inputarg` that the method is called with.

`inputarg` can be any type that is compatible within Open62541.jl, particularly builtin number types, strings, as well as UA_XXX types. Input arguments can also be arrays (for example a Vector{Float64}). Multiple arguments should be provided as a tuple.

```
JUA_CallMethodRequest(methodrequestptr::Ptr{UA_CallMethodRequest})
```

creates a `JUA_CallMethodRequest` based on the pointer `methodrequestptr`. This is a fallback method that can be used to pass `UA_CallMethodRequest`s generated via the low level interface to the higher level functions. Note that memory management remains on the C side when using this method, i.e., `methodrequestptr` needs to be manually cleaned up with `UA_CallMethodRequest_delete(methodrequestptr)` after the object is not needed anymore. It is up to the user to ensure this.

Examples:

```
j = JUA_CallMethodRequest()
j = JUA_CallMethodRequest(JUA_NodeId(0, UA_NS0ID_OBJECTSFOLDER), JUA_NodeId(1, 1234), ["Peter", "Julia"]) #one vector of strings inputarg
j = JUA_CallMethodRequest(JUA_NodeId(0, UA_NS0ID_OBJECTSFOLDER), JUA_NodeId(1, 1234), ("Claudia", 1234)]) #two input args
```

See also:

  * [`UA_MethodCallback_generate`](@ref)
  * [`UA_MethodCallback_wrap`](@ref)
  * [`JUA_Server_addNode`](@ref)
