```
aggregate_LOB_measurement(X::Union{Vector{Float64}, JVector{Float64}}, times::Vector{Time}, time_step::Period, f::Function; f_args::Tuple=(), f_kwargs::NamedTuple=NamedTuple())
```

指定された `time_step` で `f` 変換を行うことによって `X` を集約します。
