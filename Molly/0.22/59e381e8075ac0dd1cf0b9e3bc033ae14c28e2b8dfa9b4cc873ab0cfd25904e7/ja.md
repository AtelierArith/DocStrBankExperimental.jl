```
HamiltonianREMD(; <キーワード引数>)
```

[`ReplicaSystem`](@ref)上での並列ハミルトニアンレプリカ交換MD (H-REMD) シミュレーターです。

レプリカは異なるハミルトニアン、すなわち異なる相互作用を持つことが期待されます。 [`simulate!`](@ref)を呼び出す際、`assign_velocities`キーワード引数は、各レプリカに対して適切な温度でランダムな速度を割り当てるかどうかを決定します。

# 引数

  * `dt::DT`: シミュレーションの時間ステップ。
  * `temperature::T`: シミュレーションの温度。
  * `simulators::ST`: 各レプリカをシミュレートするための個別のシミュレーター。
  * `exchange_time::ET`: レプリカ交換試行の間隔時間。
