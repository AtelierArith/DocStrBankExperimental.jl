```
period(::Type{<:Period}, year::Integer, subperiod::Integer = 1)
```

Construct a period from a year, subperiod, and frequency.

These periods are represented as an Int64 number of periods since an epoch defined by the [`ExtendedDates.epoch`](@ref) function. For most period types the epoch is Saturday, January 1, year 0. For week periods, it is Monday, January 3, year 0.

```jldoctest
julia> x = period(Semester, 2022, 1)
2022-S1

julia> Dates.format(x)
"2022-S1"

julia> Date(x)
2022-01-01

julia> Date(period(Week, 0))
0000-01-03

julia> Date(period(Day, 0))
0000-01-01
```
