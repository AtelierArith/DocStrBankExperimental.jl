```
solve_mn_traditional_mld(
    data::Dict{String,<:Any},
    model_type::Type,
    solver;
    kwargs...
)::Dict{String,Any}
```

**マルチネットワーク**マルチコンダクタの従来のmld問題を`model_type`と`solver`を使用して解決します。

PowerModelsDistribution.solve*mc*modelにコールバックし、そのため、その関数に対して有効な`kwargs`を受け入れます。詳細についてはPowerModelsDistribution [ドキュメント](https://lanl-ansi.github.io/PowerModelsDistribution.jl/latest)を参照してください。
