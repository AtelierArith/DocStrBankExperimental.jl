```
worst_value_i(rpd, H, C, i, lp_solver=highs_optimizer_silent)
```

与えられた制約 w ∈ W に対して、エージェント i の最悪のペイオフを見つけます。

# 引数

  * `rpd::RepGame2` : 2人用の繰り返しゲーム。
  * `H::Matrix{Float64}` : 形状 `(nH, 2)` の行列で、ここで `nH` はサブ勾配の数です。
  * `C::Vector{Float64}` : ハイパープレーンのレベルを含む配列。
  * `i::Int` : 関心のあるプレイヤー。
  * `lp_solver` : 内部で使用される線形計画ソルバー。オプションが必要ない場合は `MathOptInterface.AbstractOptimizer` 型（例えば `HiGHS.Optimizer`）を渡すか、オプションを供給する関数（例えば `GameTheory.highs_optimizer_silent`）を渡します。

# 戻り値

  * `out::Float64` : プレイヤー i の最悪のペイオフ。
