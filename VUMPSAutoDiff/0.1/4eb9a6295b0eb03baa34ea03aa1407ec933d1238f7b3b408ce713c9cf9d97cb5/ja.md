```
DIIS_extrapolation_alg
```

DIIS外挿アルゴリズムのパラメータを表す構造体。

# フィールド

  * `M::Int`: 最大反復回数
  * `ΔM::Int`: 各DIISステップ後の追加反復回数
  * `tol::Float64`: 収束許容誤差
  * `max_diis_step::Int`: 最大DIISステップ数
  * `damping_factor::Float64`: DIIS手続きを安定させるために使用される因子
