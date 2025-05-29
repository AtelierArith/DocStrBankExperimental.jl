```
TimeAfterNow{T<:TimeType} <: BoundTime{T}
TimeAfterNow{T}(x::TimeType)
```

A time constraint for a value `x` of type `T` which must exceed the current time.

## Examples

```julia-repl
julia> using Dates

julia> TimeAfterNow{DateTime}(DateTime(2030))
2030-01-01T00:00:00

julia> TimeAfterNow{DateTime}(DateTime(2020))
ERROR: ConstraintError: constraints of type TimeAfterNow violated.
Wrong value: 2020-01-01T00:00:00 must exceed 2024-05-03T11:25:26.689.
[...]
```
