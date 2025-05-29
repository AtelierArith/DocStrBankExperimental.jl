```
get_values(abaco, ne::String, var::String)::Dict{Int,Float64}
```

Returns the ordered by time sequence of `var` values for `ne` node.

The returned values dictionary is ordered by descending time, most recent value first. The number of entries are at most equal to the  value of ages.
