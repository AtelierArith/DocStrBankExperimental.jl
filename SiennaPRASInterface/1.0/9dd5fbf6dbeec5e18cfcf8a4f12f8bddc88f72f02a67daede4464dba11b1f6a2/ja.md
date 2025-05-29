```
generate_outage_profile!(
    sys::PSY.System,
    aggregation::Type{AT},
    method::PRASCore.SequentialMonteCarlo,
) where {AT <: PSY.AggregationTopology, RM <: PRASCore.Results.ReliabilityMetric}
```

モンテカルロシミュレーションを使用してリソースの適合性を分析し、最悪のサンプルからコンポーネントのPSY.TimeSeriesForcedOutageに資産の状態を追加します。

# 引数

  * `sys::PSY.System`: PowerSystems.jl システムモデル
  * `aggregation::Type{AT}`: PRASに変換する際に使用する集約トポロジー
  * `method::PRASCore.SequentialMonteCarlo`: 使用するシミュレーション方法

# 戻り値

  * 資産の状態が利用可能なすべてのコンポーネントのPSY.TimeSeriesForcedOutageを持つPSYシステム
