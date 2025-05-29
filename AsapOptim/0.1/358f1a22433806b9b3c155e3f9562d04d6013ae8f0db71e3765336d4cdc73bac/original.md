```
replace_values(values::Vector{Float64}, indices::Vector{Int64}, newvalues::Vector{Float64})
```

Replace the values of `values[indices]` with the values in `newvalues` in a differentiable way. Does NOT perform any bounds checking or vector length consistency. This should be done before calling this function.
