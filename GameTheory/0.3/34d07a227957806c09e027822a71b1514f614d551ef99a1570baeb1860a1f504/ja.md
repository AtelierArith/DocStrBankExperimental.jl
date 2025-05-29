```
dominated_actions(player; tol=1e-8,
                  lp_solver=GameTheory.highs_optimizer_silent)
```

いくつかの混合行動によって厳密に支配される行動のベクトルを返します。

# 引数

  * `player::Player` : プレイヤーインスタンス。
  * `tol::Real` : 支配を決定する際に使用される許容レベル。
  * `lp_solver::Union{Type{<:MathOptInterface.AbstractOptimizer},Function}` : 内部で使用される線形計画法ソルバー。オプションが必要ない場合は`MathOptInterface.AbstractOptimizer`型（例えば`HiGHS.Optimizer`）を渡すか、オプションを提供する関数（例えば`GameTheory.highs_optimizer_silent`）を渡します。

# 戻り値

  * `out::Vector{Int}` : 各々がいくつかの混合行動によって厳密に支配される純粋な行動を表す整数のベクトル。
