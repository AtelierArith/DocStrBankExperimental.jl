```
UA_MethodCallback_wrap(f::Function)
```

wraps a simple Julia function that operates on inputs into the correct format to be supplied to `UA_MethodCallback_generate`.

`f` must be a Julia function with the following signature:

```
f(input1::Any, input2::Any, input3::Any, ...) -> output::Union{Any, Tuple{Any, ...}}
```

where `Any` means that in principle any type is allowed. However, since Open62541 is based on C the corresponding method node is *always* configured to only work with a specific combination of input types.

If larger flexibility is needed than just working on the inputs given to a method node, see `UA_MethodCallback_generate`.

See also:

[`UA_MethodCallback_generate`](@ref)

[`JUA_Argument`](@ref)

[`JUA_Server_addNode`](@ref)

Example:

```
function simple_hello(name, adjective)
    assembledstring = "Hello "*name*", you are "*adjective
    return assembledstring
end 
```

which can be attached to a a method node that expects a function that takes two strings as inputs and one string as output.
