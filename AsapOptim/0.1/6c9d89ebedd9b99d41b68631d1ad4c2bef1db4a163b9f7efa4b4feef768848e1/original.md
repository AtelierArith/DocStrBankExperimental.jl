```
add_values(values::Vector{Float64}, indices::Vector{Int64}, increments::Vector{Float64})
```

Add the values of `increments` to the current values in `values` at `indices`. Does NOT perform any bounds checking or vector length consistency. This should be done before calling this function.
