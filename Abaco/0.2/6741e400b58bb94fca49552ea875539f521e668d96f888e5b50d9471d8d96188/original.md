```
last_point(abaco, ne::String, var::String)::Union{Nothing, Missing, Tuple{Int,Float64}}
```

Returns the most recent in time value for the `ne` node metric `var` as a tuple (time, value).

If the node `ne` is unknown returns `nothing` and if there are not values for metric `var` returns `missing`.
