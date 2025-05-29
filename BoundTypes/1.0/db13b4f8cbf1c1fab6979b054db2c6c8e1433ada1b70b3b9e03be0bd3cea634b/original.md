```
TimeBeforeNow{T<:TimeType} <: BoundTime{T}
TimeBeforeNow{T}(x::TimeType)
```

A time constraint for a value `x` of type `T` which must precede the current time.

## Examples

```julia-repl
julia> using Dates

julia> TimeBeforeNow{DateTime}(DateTime(2020))
2020-01-01T00:00:00

julia> TimeBeforeNow{DateTime}(DateTime(2030))
ERROR: ConstraintError: constraints of type TimeBeforeNow violated.
Wrong value: 2030-01-01T00:00:00 must precede 2024-05-03T11:36:37.848.
[...]
```
