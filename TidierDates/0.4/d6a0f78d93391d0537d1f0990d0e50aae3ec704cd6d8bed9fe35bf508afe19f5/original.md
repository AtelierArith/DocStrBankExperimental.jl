```
am(dt::DateTime)::Bool
```

Checks if the time is in the morning.

# Arguments

`dt`: A DateTime object

# Returns

A boolean indicating whether the time is in the morning.

# Examples

```jldoctest
julia> am(DateTime(2023, 6, 15, 9, 30, 0))
true

julia> am(DateTime(2023, 6, 15, 8, 30, 0))
true
```
