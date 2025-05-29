```
StringCustomBound{T<:AbstractString,B} <: BoundString{T}
StringCustomBound{T,B}(x::AbstractString)
```

A string constraint for a value `x` of type `T` using custom function `B`. Function `B` should only accept object `x` and return `true` or `false` (or throw a custom [`ConstraintError`](@ref)).

## Examples

```julia-repl
julia> StringCustomBound{String,x -> length(x) > 5}("abcdef")
"abcdef"

julia> StringCustomBound{String,x -> length(x) > 5}("abc")
ERROR: ConstraintError: constraints of type StringCustomBound violated.
Wrong value: Custom constraint '#5' violated for value "abc" of type String.
[...]
```
