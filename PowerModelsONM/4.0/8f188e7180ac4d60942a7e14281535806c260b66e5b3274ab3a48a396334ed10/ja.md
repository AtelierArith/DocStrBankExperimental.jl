```
run_stability_analysis(
    network::Dict{String,<:Any},
    inverters::Dict{String,<:Any},
    solver;
    formulation::Type=PMD.ACRUPowerModel,
    switching_solutions::Union{Missing,Dict{String,<:Any}}=missing,
    distributed::Bool=false
)::Dict{String,Bool}
```

小信号安定性分析をPowerModelsStabilityを使用して実行し、各タイムステップ構成が安定しているかどうかを判断します。

`inverters`は、[`parse_inverters`](@ref parse_inverters)を使用してすでに解析されたインバーターファイルです。

定式化は`formulation`で指定できますが、解の中に「vm」と「va」変数が含まれている必要があります。そうでない場合は、`PowerModelsDistribution.sol_data_model!`が電圧変数を極座標に変換することをサポートしている必要があります。

安定性分析のための`solver`（NLP OPF）
