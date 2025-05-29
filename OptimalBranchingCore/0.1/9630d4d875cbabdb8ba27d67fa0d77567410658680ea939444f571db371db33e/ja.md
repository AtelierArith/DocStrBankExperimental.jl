```
LPSolver <: AbstractSetCoverSolver
LPSolver(; optimizer = HiGHS.Optimizer, max_itr::Int = 20, γ0::Float64 = 2.0, verbose::Bool = false)
```

集合被覆問題のための線形計画法ソルバー。

### フィールド

  * `optimizer`: 使用するオプティマイザー。
  * `max_itr::Int`: 実行される最大反復回数。
  * `γ0::Float64`: 初期γ値。
  * `verbose::Bool`: ソルバーの出力を表示するかどうか。
