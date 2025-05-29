```
pm(dt::DateTime)::Bool
```

Checks if the time is in the afternoon.

# Arguments

`dt`: A DateTime object

# Returns

A boolean indicating whether the time is in the afternoon.

# Examples

```jldoctest
julia> pm(DateTime(2023, 6, 15, 9, 30, 0))
false

julia> pm(DateTime(2023, 6, 15, 8, 30, 0))
false
```
