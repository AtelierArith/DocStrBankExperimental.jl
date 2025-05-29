```
last_value(abaco, ne::String, var::String)::Union{Nothing, Missing, Float64}
```

Returns the most recent in time value for the `ne` node metric `var`

If the node `ne` is unknown returns `nothing` and if there are not values for metric `var` returns `missing`.
