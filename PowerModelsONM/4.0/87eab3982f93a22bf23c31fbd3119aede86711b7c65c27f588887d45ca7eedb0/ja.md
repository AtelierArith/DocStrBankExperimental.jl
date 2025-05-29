```
generate_load_robust_partitions(data::Dict{String,<:Any}, contingencies::Set{<:Dict{String,<:Any}}, model_type::Type, solver; N=2, ΔL=0.1, kwargs...)
```

`contingencies`のためのロバストなパーティションを生成し、同時に負荷の不確実性（NとΔLによって定義される）も考慮します。
