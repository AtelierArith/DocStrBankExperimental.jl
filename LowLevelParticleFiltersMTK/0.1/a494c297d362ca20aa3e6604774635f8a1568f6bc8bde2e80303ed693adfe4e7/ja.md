```
StateEstimationSolution(kfsol, prob)
```

`KalmanFilteringSolution`オブジェクトに対してシンボリックインデックスを提供するソリューションオブジェクトです。

## フィールド:

  * `sol`:  `KalmanFilteringSolution`オブジェクト。
  * `prob`: `StateEstimationProblem`オブジェクト。

## 例

```julia
sol = StateEstimationSolution(kfsol, prob)
sol[model.x]                 # 変数でインデックス
sol[model.y^2]               # 式でインデックス
sol[model.y^2, dist=true]    # 提供された式の事後確率分布を取得
sol[model.y^2, Nsamples=100] # 提供された式の事後分布から100サンプルを引く
```
