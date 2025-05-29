```
TimePeriodBeforeNow{T<:TimeType,P} <: BoundTime{T}
TimePeriodBeforeNow{T,P}(x::TimeType)
```

A time constraint for a value `x` of type `T` which must precede the current time during period `P`.

## Examples

```julia-repl
julia> using Dates

julia> TimePeriodBeforeNow{DateTime,Year(10)}(DateTime(2020))
2020-01-01T00:00:00

julia> TimePeriodBeforeNow{DateTime,Year(10)}(DateTime(2030))
ERROR: ConstraintError: constraints of type TimePeriodBeforeNow violated.
Wrong value: 2030-01-01T00:00:00 must be in interval between 2014-05-03T11:38:35.124 and 2024-05-03T11:38:35.124.
[...]
```
