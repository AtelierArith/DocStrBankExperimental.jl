```
PhaseEquil{FT} <: AbstractPhaseEquil
```

熱力学的平衡を仮定した熱力学的状態（したがって、飽和調整が必要な場合があります）。

# コンストラクタ

```
PhaseEquil(param_set, ρ, e_int, q_tot)
```

# フィールド

  * `ρ`: 空気の密度（潜在的に湿った）
  * `p`: 空気圧
  * `e_int`: 内部エネルギー
  * `q_tot`: 総比湿度
  * `T`: 温度: [`saturation_adjustment`](@ref) を介して計算される
