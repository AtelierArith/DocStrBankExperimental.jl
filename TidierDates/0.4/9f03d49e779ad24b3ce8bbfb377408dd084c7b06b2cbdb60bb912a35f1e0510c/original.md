```
days_in_month(date::Date)::Int
```

Returns the number of days in the month.

# Arguments

`date`: A Date object

# Returns

An integer representing the number of days in the month.

# Examples

```jldoctest
julia> days_in_month(Date(2023, 6, 15))
30

julia> days_in_month(Date(2020, 2, 29))
29

julia> days_in_month(Date(2019, 2, 28))
28

julia> days_in_month(Date(2016, 2, 3))
29
```
