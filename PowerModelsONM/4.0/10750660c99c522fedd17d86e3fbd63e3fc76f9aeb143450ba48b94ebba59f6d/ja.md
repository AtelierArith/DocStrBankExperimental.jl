```
solve_mn_opf(
    data::Dict{String,<:Any},
    model_type::Type,
    solver;
    kwargs...
)::Dict{String,Any}
```

トランスフォーマータップとコンデンサー制御を用いたマルチネットワークOPFを解決します。
