```
generate_load_robust_partitions(data::Dict{String,<:Any}, contingencies::Set{<:Dict{String,<:Any}}, model_type::Type, solver; N=2, ΔL=0.1, kwargs...)
```

Generate robust partitions for `contingencies` while also considering load uncertainty (defined by N and ΔL).
