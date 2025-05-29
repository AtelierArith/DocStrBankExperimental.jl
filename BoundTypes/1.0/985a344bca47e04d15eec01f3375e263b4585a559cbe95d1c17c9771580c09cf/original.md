```
NumberCustomBound{T<:Number,B} <: BoundNumber{T}
NumberCustomBound{T,B}(x::Number)
```

A number constraint for a value `x` of type `T` using custom function `B`. Function `B` should only accept object `x` and return `true` or `false` (or throw a custom [`ConstraintError`](@ref)).

## Examples

```julia-repl
julia> NumberCustomBound{Float64,x -> x % 2 == 0}(10.0)
10.0

julia> NumberCustomBound{Float64,x -> x % 2 == 0}(13.0)
ERROR: ConstraintError: constraints of type NumberCustomBound violated.
Wrong value: Custom constraint '#7' violated for value "13.0" of type Float64.
[...]
```
