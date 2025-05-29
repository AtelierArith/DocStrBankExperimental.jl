```
TimeCustomBound{T<:TimeType,B} <: BoundTime{T}
TimeCustomBound{T,B}(x::TimeType)
```

A time constraint for a value `x` of type `T` using custom function `B`. Function `B` should only accept object `x` and return `true` or `false` (or throw a custom [`ConstraintError`](@ref)).

## Examples

```julia-repl
julia> using Dates

julia> TimeCustomBound{DateTime,isleapyear}(DateTime(2024))
2024-01-01T00:00:00

julia> TimeCustomBound{DateTime,isleapyear}(DateTime(2023))
ERROR: ConstraintError: constraints of type TimeCustomBound violated.
Wrong value: Custom constraint 'isleapyear' violated for value "2023-01-01T00:00:00" of type DateTime.
[...]
```
