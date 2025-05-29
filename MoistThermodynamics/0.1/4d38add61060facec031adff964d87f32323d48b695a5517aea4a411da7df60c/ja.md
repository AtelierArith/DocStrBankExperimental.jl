```
PhaseDry{FT} <: ThermodynamicState
```

乾燥熱力学状態（`q_tot = 0`）。

# コンストラクタ

```
PhaseDry(e_int, ρ)
```

# フィールド

  * `param_set`: パラメータセット（例：惑星パラメータ）
  * `e_int`: 内部エネルギー
  * `ρ`: 乾燥空気の密度
