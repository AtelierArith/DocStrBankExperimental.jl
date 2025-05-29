```
 PhaseNonEquil{FT} <: ThermodynamicState
```

熱力学的非平衡を仮定した熱力学的状態（したがって、温度は直接計算できます）。

# コンストラクタ

```
PhaseNonEquil(param_set, e_int, q::PhasePartition, ρ)
```

# フィールド

  * `e_int`: 内部エネルギー
  * `ρ`: 空気の密度（潜在的に湿った）
  * `q`: 相分割
