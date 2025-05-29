```julia
generate_outage_profile!(
    sys::PowerSystems.System,
    template::SiennaPRASInterface.RATemplate,
    method::PRASCore.Simulations.SequentialMonteCarlo
) -> PowerSystems.System

```

モンテカルロシミュレーションを使用してリソースの適合性を分析し、最悪のサンプルからの資産の状態をコンポーネントのPSY.TimeSeriesForcedOutageに追加します。

# 引数

  * `sys::PSY.System`: PowerSystems.jlシステムモデル
  * `template::RATemplate`: PRAS問題テンプレート
  * `method::PRASCore.SequentialMonteCarlo`: 使用するシミュレーション方法

# 戻り値

  * 資産の状態が利用可能なすべてのコンポーネントのPSY.TimeSeriesForcedOutageを持つPSYシステム
