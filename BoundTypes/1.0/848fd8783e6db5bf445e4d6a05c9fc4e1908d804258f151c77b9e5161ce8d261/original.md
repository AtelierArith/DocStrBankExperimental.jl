```
TimeBeforeOrEqual{T<:TimeType,V} <: BoundTime{T}
TimeBeforeOrEqual{T,V}(x::TimeType)
```

A time constraint for a value `x` of type `T` which must precede or be equal to the time `V`.

## Examples

```jldoctest
julia> using Dates

julia> TimeBeforeOrEqual{DateTime,DateTime(2023)}(DateTime(2022))
2022-01-01T00:00:00

julia> TimeBeforeOrEqual{DateTime,DateTime(2023)}(DateTime(2023))
2023-01-01T00:00:00

julia> TimeBeforeOrEqual{DateTime,DateTime(2023)}(DateTime(2024))
ERROR: ConstraintError: constraints of type TimeBeforeOrEqual violated.
Wrong value: 2024-01-01T00:00:00 must precede or be equal to 2023-01-01T00:00:00.
[...]
```
