```
solve_traditional_mld(
    data::Dict{String,<:Any},
    model_type::Type,
    solver;
    kwargs...
)::Dict{String,Any}
```

`model_type` と `solver` を使用して、マルチコンダクタの従来の mld 問題を解決します。

PowerModelsDistribution.solve*mc*model にコールバックし、そのため、その関数に対して有効な `kwargs` を受け入れます。詳細については、PowerModelsDistribution [documentation](https://lanl-ansi.github.io/PowerModelsDistribution.jl/latest) を参照してください。
