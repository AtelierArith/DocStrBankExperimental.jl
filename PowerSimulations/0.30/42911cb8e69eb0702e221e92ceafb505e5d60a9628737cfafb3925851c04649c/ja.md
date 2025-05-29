```julia
solve!(
    model::PowerSimulations.DecisionModel;
    export_problem_results,
    console_level,
    file_level,
    disable_timer_outputs,
    export_optimization_problem,
    kwargs...
) -> InfrastructureSystems.Simulation.RunStatusModule.RunStatus

```

デフォルトの解決メソッドは、DecisionModel{<: DecisionProblem}の要件に準拠したモデル用です。

これは、モデルがまだ構築されていない場合に`build!`を呼び出します。すべてのキーワード引数はその関数に転送されます。

# 引数

  * `model::OperationModel = model`: 操作モデル
  * `export_problem_results::Bool = false`: 真の場合、OptimizationProblemResults DataFramesをCSVファイルにエクスポートします。シミュレーション中の解決時間を短縮します。
  * `console_level = Logging.Error`:
  * `file_level = Logging.Info`:
  * `disable_timer_outputs = false` : タイミング出力の有効/無効
  * `export_optimization_problem::Bool = true`: 真の場合、モデルをファイルにシリアライズして後で再実行できるようにします。

# 例

```julia
results = solve!(OpModel)
results = solve!(OpModel, export_problem_results = true)
```
