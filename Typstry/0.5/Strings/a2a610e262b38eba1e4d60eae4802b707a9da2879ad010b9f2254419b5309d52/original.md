```
ContextError <: Exception
ContextError(::Type, ::Type, ::Symbol)
```

An `Exception` indicating that a [`context`](@ref) key returned a value of an incorrect type.

# Examples

```jldoctest
julia> ContextError(Mode, String, :mode)
ContextError(Mode, String, :mode)
```
