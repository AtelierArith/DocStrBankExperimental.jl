```
leap_year(date::Date)::Bool
leap_year(date::Int)::Bool
```

Checks if the year is a leap year.

# Arguments

`date`: A Date object or an integer representing the year.

# Returns

A boolean indicating whether the year is a leap year.

# Examples

```jldoctest
julia> leap_year(Date(2023, 6, 15))
false

julia> leap_year(2020)
true
```
