```
TemperatureREMD(; <キーワード引数>)
```

[`ReplicaSystem`](@ref)上での並列温度レプリカ交換MD (T-REMD) シミュレーションのシミュレーターです。

[Sugita and Okamoto 1999](https://doi.org/10.1016/S0009-2614(99)01123-9)を参照してください。対応する[`ReplicaSystem`](@ref)は、シミュレーターの温度の数と同じ数のレプリカを持っている必要があります。[`simulate!`](@ref)を呼び出す際、`assign_velocities`キーワード引数は、各レプリカの適切な温度でランダムな速度を割り当てるかどうかを決定します。

# 引数

  * `dt::DT`: シミュレーションの時間ステップ。
  * `temperatures::TP`: レプリカに対応する温度。
  * `simulators::ST`: 各レプリカをシミュレートするための個別のシミュレーター。
  * `exchange_time::ET`: レプリカ交換試行の間隔時間。
