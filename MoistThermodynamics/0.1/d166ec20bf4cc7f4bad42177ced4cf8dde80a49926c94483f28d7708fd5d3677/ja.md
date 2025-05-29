```
PhasePartition_equil(T, ρ, q_tot)
```

平衡状態の相を分割し、[`liquid_fraction`](@ref) 関数を使用して [`PhasePartition`](@ref) オブジェクトを返します。ここで

  * `T` 温度
  * `ρ` （湿った）空気の密度
  * `q_tot` 総比湿度

残りの `q.tot - q.liq - q.ice` は蒸気の比湿度です。
