```
is_dominated(player, action; tol=1e-8,
             lp_solver=GameTheory.highs_optimizer_silent)
```

`action` がいくつかの混合行動によって厳密に支配されているかどうかを判断します。

# 引数

  * `player::Player` : プレイヤーインスタンス。
  * `action::PureAction` : 純粋な行動を表す整数。
  * `tol::Real` : 支配を判断する際に使用される許容レベル。
  * `lp_solver` : 内部で使用される線形計画ソルバー。オプションが必要ない場合は `MathOptInterface.AbstractOptimizer` 型（例えば `HiGHS.Optimizer`）を渡すか、オプションを提供する関数（例えば `GameTheory.highs_optimizer_silent`）を渡します。

# 戻り値

  * `::Bool` : `action` がいくつかの混合行動によって厳密に支配されている場合は真、そうでない場合は偽。
