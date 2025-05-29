```julia
solve!(
    step::Int64,
    model::PowerSimulations.DecisionModel,
    start_time::Dates.DateTime,
    store::PowerSimulations.SimulationStore;
    exports
) -> InfrastructureSystems.Simulation.RunStatusModule.RunStatus

```

シミュレーション内で使用されるDecisionModelのデフォルト解法メソッド。DecisionModel{<: DecisionProblem}の要件に準拠した問題を解決します。

# 引数

  * `step::Int`: シミュレーションステップ
  * `model::OperationModel`: 操作モデル
  * `start_time::Dates.DateTime`: シミュレーションステップの初期時間。
  * `store::SimulationStore`: シミュレーション出力ストア

# 受け入れられるキーワード

  * `exports`: 出力のリアルタイムエクスポート。賢く使用してください。シミュレーション時間に悪影響を及ぼす可能性があります。
