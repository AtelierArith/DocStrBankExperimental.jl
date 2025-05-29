```julia
solve!(
    step::Int64,
    model::PowerSimulations.EmulationModel,
    start_time::Dates.DateTime,
    store::PowerSimulations.SimulationStore;
    exports
) -> InfrastructureSystems.Simulation.RunStatusModule.RunStatus

```

シミュレーション内で使用されるEmulationModelのデフォルトのsolveメソッド。DecisionModel{<: DecisionProblem}の要件に準拠した問題を解決します。

# 引数

  * `step::Int`: シミュレーションステップ
  * `model::OperationModel`: 操作モデル
  * `start_time::Dates.DateTime`: シミュレーション時間におけるシミュレーションステップの初期時間。
  * `store::SimulationStore`: シミュレーション出力ストア
  * `exports = nothing`: 出力のリアルタイムエクスポート。賢く使用してください。シミュレーション時間に悪影響を与える可能性があります。
