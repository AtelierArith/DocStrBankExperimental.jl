```
FiniteReservoirProblem(eq, rstop, tstop; i, b, capacity) <: AbstractFiniteProblem
```

`eq`を領域`0 ≤ r ≤ rstop`でモデル化し、初期条件`i`と貯水池境界条件を持ちます。

# 引数

  * `eq`: 解くべき方程式。
  * `rstop`: 領域の長さ。
  * `tstop=Inf`: 最終時間。`Inf`の場合、解は定常状態に達するまで計算されます。

# キーワード引数

  * `i`: 初期値。
  * `b`: 境界値。
  * `capacity`: 貯水池の容量。
