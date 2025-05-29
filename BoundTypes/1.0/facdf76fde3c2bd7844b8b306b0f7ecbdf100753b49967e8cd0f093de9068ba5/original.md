```
TimeBefore{T<:TimeType,V} <: BoundTime{T}
TimeBefore{T,V}(x::TimeType)
```

A time constraint for a value `x` of type `T` which must precede the time `V`.

## Examples

```jldoctest
julia> using Dates

julia> TimeBefore{DateTime,DateTime(2023)}(DateTime(2022))
2022-01-01T00:00:00

julia> TimeBefore{DateTime,DateTime(2023)}(DateTime(2024))
ERROR: ConstraintError: constraints of type TimeBefore violated.
Wrong value: 2024-01-01T00:00:00 must precede 2023-01-01T00:00:00.
[...]
```
