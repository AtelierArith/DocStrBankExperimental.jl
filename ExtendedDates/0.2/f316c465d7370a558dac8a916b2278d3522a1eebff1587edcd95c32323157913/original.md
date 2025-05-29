```
year(::UTInstant{<:Period})
```

The subperiod of a period within a year. Numbering starts at one.

```jldoctest
julia> subperiod(period(Day, 1960, 12))
12

julia> Date(period(Day, 1960, 12))
1960-01-12
```
