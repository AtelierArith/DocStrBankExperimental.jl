```
solve_fault_study(case::Dict{String,<:Any}, fault_studies::Dict{String,<:Any}, solver; kwargs...)::Dict{String,Any}
```

`fault_studies`内の一連の故障研究を解決します。これは、最適化`solver`が与えられた場合に、伝送（matpower）データセットのために[`build_fault_study`](@ref build_fault_study)によって生成されます。

`kwargs`は、PowerModelsのrun_model関数に対する有効なキーワード引数であれば何でも使用できます。
