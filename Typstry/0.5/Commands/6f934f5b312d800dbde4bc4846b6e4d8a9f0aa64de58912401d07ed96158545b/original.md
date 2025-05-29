```
TypstError <: Exception
TypstError(::TypstCommand)
```

An `Exception` indicating a failure to [`run`](@ref) a [`TypstCommand`](@ref).

# Examples

```jldoctest
julia> TypstError(typst``)
TypstError(typst``)
```
