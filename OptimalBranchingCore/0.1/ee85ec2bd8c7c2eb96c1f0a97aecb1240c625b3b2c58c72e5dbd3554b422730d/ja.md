```
IPSolver <: AbstractSetCoverSolver
IPSolver(; optimizer = HiGHS.Optimizer, max_itr::Int = 20, γ0::Float64 = 2.0, verbose::Bool = false)
```

集合被覆問題のための整数プログラミングソルバー。

### フィールド

  * `optimizer`: 使用するオプティマイザー。
  * `max_itr::Int`: 実行される最大反復回数。
  * `γ0::Float64`: 初期γ値。
  * `verbose::Bool`: ソルバーの出力を表示するかどうか。
