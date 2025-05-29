```
TimeInterval{T<:TimeType,A,L,R,B} <: BoundTime{T}
TimeInterval{T,A,L,R,B}(x::TimeType)
```

A time constraint for a value `x` of type `T` which belongs to an interval between times `A` and `B`. Parameters `L` and `R` are the comparison functions e.g `<` or `<=` which determine whether interval boundaries are included.

## Examples

```jldoctest
julia> using Dates

julia> TimeInterval{DateTime,DateTime(2023),<,<,DateTime(2025)}(DateTime(2024))
2024-01-01T00:00:00

julia> TimeInterval{DateTime,DateTime(2023),<,<=,DateTime(2025)}(DateTime(2025))
2025-01-01T00:00:00

julia> TimeInterval{DateTime,DateTime(2023),<,<,DateTime(2025)}(DateTime(2025))
ERROR: ConstraintError: constraints of type TimeInterval violated.
Wrong value: 2025-01-01T00:00:00 must be in interval between 2023-01-01T00:00:00 and 2025-01-01T00:00:00.
[...]
```
