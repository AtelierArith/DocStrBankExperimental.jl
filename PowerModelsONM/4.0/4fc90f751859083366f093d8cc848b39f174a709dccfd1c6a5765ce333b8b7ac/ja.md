```
solve_robust_block_mld(
    data::Dict{String,<:Any},
    model_type::Type,
    solver;
    N::Int, ΔL::Float64,
    kwargs...
)::Dict{String, Dict{String,Any}}
```

ロバスト（Nシナリオおよび±ΔL負荷不確実性）分割問題（混合整数）を解決し、`model_type`および`solver`を使用して不確実性を考慮します。デフォルトのシナリオ数は2に設定されており、負荷不確実性は±10%（基準負荷の周り）で、シナリオはgenerate*load*scenarios()を使用して生成されます。
