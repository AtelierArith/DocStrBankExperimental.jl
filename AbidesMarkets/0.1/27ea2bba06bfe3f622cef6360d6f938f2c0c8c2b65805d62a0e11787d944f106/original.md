```
aggregate_LOB_measurement(X::Union{Vector{Float64}, JVector{Float64}}, times::Vector{Time}, time_step::Period, f::Function; f_args::Tuple=(), f_kwargs::NamedTuple=NamedTuple())
```

Aggregate `X` by taking its `f` transformation at the specified `time_step`.
