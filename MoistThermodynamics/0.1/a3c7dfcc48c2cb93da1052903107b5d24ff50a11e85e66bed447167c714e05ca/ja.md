```
PhaseEquil{FT} <: ThermodynamicState
```

熱力学的平衡を仮定した熱力学状態（したがって、飽和調整が必要な場合があります）。

# コンストラクタ

```
PhaseEquil(e_int, ρ, q_tot)
```

# フィールド

  * `param_set`: パラメータセット（例：惑星パラメータ）
  * `e_int`: 内部エネルギー
  * `ρ`: 空気の密度（湿気を含む可能性あり）
  * `q_tot`: 総比湿度
  * `T`: 温度：[`saturation_adjustment`](@ref)を介して計算される
