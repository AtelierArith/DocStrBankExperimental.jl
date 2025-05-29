```
solve_robust_block_mld(
    data::Dict{String,<:Any},
    model_type::Type,
    solver,
    load_scenarios::Dict{Int, Dict{Any, Any}}
    kwargs...
)::Dict{String, Dict{String,Any}}
```

不確実性を考慮したロバストな分割問題（混合整数）を解決します。`model_type`、`solver`、およびユーザー指定の負荷不確実性データ`load_scenarios`（基本負荷値の周りの許可された不確実性範囲として提供する必要があります。これは最初のシナリオです）。
