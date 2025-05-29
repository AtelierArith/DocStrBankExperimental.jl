非線形問題に対するニュートン-クリロフアルゴリズムの適用から得られた解を保持する構造体。

例えば

```
sol = newton(prob, NewtonPar())
```

## フィールド

  * `u::Any`: 解
  * `prob::Any`: 非線形問題、通常は `BifurcationProblem`
  * `residuals::Any`: 残差の列
  * `converged::Bool`: アルゴリズムは収束したか？
  * `itnewton::Int64`: ニュートンステップの数
  * `itlineartot::Any`: 総線形反復回数

## メソッド

  * `converged(sol)` 解が収束したかどうかを返す。
