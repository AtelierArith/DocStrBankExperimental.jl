```
FiniteDirichletProblem(eq, rstop[, tstop]; i, b) <: AbstractFiniteProblem
```

`eq`をドメイン`0 ≤ r ≤ rstop`でモデル化し、初期条件`i`と境界条件`b`を設定します。

# 引数

  * `eq`: 解く方程式。
  * `rstop`: ドメインの長さ。
  * `tstop=Inf`: 最終時間。`Inf`の場合、定常状態に達するまで解が計算されます。

# キーワード引数

  * `i`: 初期値。
  * `b`: 境界値。
