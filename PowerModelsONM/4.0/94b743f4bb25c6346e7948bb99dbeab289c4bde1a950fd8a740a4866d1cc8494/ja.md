```
run_fault_studies(
    network::Dict{String,<:Any},
    solver;
    faults::Dict{String,<:Any}=Dict{String,Any}(),
    switching_solutions::Union{Missing,Dict{String,<:Any}}=missing,
    dispatch_solution::Union{Missing,Dict{String,<:Any}}=missing,
    distributed::Bool=false
)::Dict{String,Any}
```

ieee13*faults.jsonで定義された故障研究を実行します。故障ファイルが提供されていない場合、自動的に`PowerModelsProtection.build*mc*fault*study`を使用して故障を生成します。

ストレージはまだPowerModelsProtectionのIVRUモデルではサポートされていないため、ストレージを制限された発電機に変換します。

実際の故障研究を解決するために[`run_fault_study`](@ref run_fault_study)を使用します。

`solver`は、使用されるインスタンス化されたソルバーを決定します、`"nlp_solver"`または`"juniper_solver"`です。
