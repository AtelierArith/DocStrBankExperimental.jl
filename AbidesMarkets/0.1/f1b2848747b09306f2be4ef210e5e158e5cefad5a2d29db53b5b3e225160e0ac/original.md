```
aggregate_LOB_measurement_avg(X::Union{Vector{Float64}, JVector{Float64}}, times::Vector{Time}, time_step::Period)
```

Aggregate `X` by returing the average (non-overlapping) measurement taken at the specified `time_step`.
