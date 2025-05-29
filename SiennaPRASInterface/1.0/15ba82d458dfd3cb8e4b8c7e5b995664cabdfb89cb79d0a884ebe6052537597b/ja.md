```julia
generate_outage_profile!(
    sys::PowerSystems.System,
    method::PRASCore.Simulations.SequentialMonteCarlo
) -> PowerSystems.System

```

モンテカルロシミュレーションを使用してリソースの適合性を分析し、最悪のサンプルからコンポーネントのPSY.TimeSeriesForcedOutageに資産の状態を追加します。

PSY.Area AggregationTopologyを使用したデフォルトテンプレートを使用します。

# 引数

  * `sys::PSY.System`: PowerSystems.jlシステムモデル
  * `method::PRASCore.SequentialMonteCarlo`: 使用するシミュレーション方法

# 戻り値

```
- 資産の状態が利用可能なすべてのコンポーネントのPSY.TimeSeriesForcedOutageを持つPSYシステム
```
