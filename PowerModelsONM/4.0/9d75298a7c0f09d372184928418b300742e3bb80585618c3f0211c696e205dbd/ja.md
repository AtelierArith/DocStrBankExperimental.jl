```
run_stability_analysis!(
    args::Dict{String,<:Any};
    validate::Bool=true,
    formulation::Type=PMD.ACRUPowerModel,
    solver::String="nlp_solver"
)::Dict{String,Bool}
```

小信号安定性分析をPowerModelsStabilityを使用して実行し、各タイムステップの構成が安定しているかどうかを判断します。結果は`args["stability_results"]`に格納され、[`entrypoint`](@ref entrypoint)で使用されます。[`run_stability_analysis`](@ref run_stability_analysis)を使用します。

`validate`がtrueの場合、生のインバーターデータはJSONスキーマに対して検証されます。

`formulation`で定式化を指定できますが、解の中に`"vm"`および`"va"`変数が含まれている必要があります。そうでない場合は、`PowerModelsDistribution.sol_data_model!`が電圧変数を極座標に変換することをサポートしている必要があります。

`solver`（デフォルト: `"nlp_solver"`）は、安定性分析に使用する`args["solvers"]`内のソルバーを指定します（NLP OPF）。
