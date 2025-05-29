```
TimeAfter{T<:TimeType,V} <: BoundTime{T}
TimeAfter{T,V}(x::TimeType)
```

A time constraint for a value `x` of type `T` which must exceed the time `V`.

## Examples

```jldoctest
julia> using Dates

julia> TimeAfter{DateTime,DateTime(2023)}(DateTime(2024))
2024-01-01T00:00:00

julia> TimeAfter{DateTime,DateTime(2023)}(DateTime(2022))
ERROR: ConstraintError: constraints of type TimeAfter violated.
Wrong value: 2022-01-01T00:00:00 must exceed 2023-01-01T00:00:00.
[...]
```
