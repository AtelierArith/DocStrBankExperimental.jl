```julia
run!(
    model::PowerSimulations.EmulationModel;
    export_problem_results,
    console_level,
    file_level,
    disable_timer_outputs,
    export_optimization_model,
    kwargs...
) -> InfrastructureSystems.Simulation.RunStatusModule.RunStatus

```

EmulationModel{<: EmulationProblem} の要件に準拠した問題のデフォルト実行メソッド

これは、モデルがまだ構築されていない場合に `build!` を呼び出します。すべてのキーワード引数はその関数に転送されます。

# 引数

  * `model::EmulationModel = model`: エミュレーションモデル
  * `optimizer::MOI.OptimizerWithAttributes`: モデルを解決するために使用される最適化器
  * `executions::Int`: エミュレーター実行の実行回数
  * `export_problem_results::Bool`: true の場合、OptimizationProblemResults DataFrames を CSV ファイルにエクスポートします。
  * `output_dir::String`: モデルがまだ構築されていない場合に必要で、そうでない場合は無視されます
  * `enable_progress_bar::Bool`: プログレスバーの印刷を有効/無効にします
  * `export_optimization_model::Bool`: true の場合、モデルをファイルにシリアライズして後で再実行できるようにします。

# 例

```julia
status = run!(model; optimizer = HiGHS.Optimizer, executions = 10)
status = run!(model; output_dir = ./model_output, optimizer = HiGHS.Optimizer, executions = 10)
```
