```
NewtonRaphson <: AbstractNonLinearSolver
```

ニュートン-ラフソンアルゴリズム。

### 属性

  * `maxiter::Int` (デフォルト 20): 最大反復回数
  * `tol::Float64` (デフォルト `1e-8`): アルゴリズムの許容誤差
  * `verbose::Int` (デフォルト `0`): 詳細レベル
