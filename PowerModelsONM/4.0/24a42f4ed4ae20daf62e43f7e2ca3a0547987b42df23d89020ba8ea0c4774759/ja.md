```
solve_mn_block_mld(
    data::Dict{String,<:Any},
    model_type::Type,
    solver;
    kwargs...
)::Dict{String,Any}
```

**マルチネットワーク** マルチコンダクタ最適スイッチング（混合整数）問題を `model_type` と `solver` を使用して解決します。

PowerModelsDistribution.solve*mc*model にコールバックし、そのため、その関数に対して有効な `kwargs` を受け入れます。詳細については、PowerModelsDistribution [ドキュメント](https://lanl-ansi.github.io/PowerModelsDistribution.jl/latest) を参照してください。
