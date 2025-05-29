```
SdofFreeTimeProblem(sdof, u0, t)
```

sdofシステムの時間問題のデータを含む構造体

**フィールド**

  * `sdof::Sdof`: Sdof構造体
  * `u0::AbstractVector`: 初期条件

      * `x0`: 初期変位 [m]
      * `v0`: 初期速度 [m/s]
  * `t::AbstractRange`: 応答を評価する時間点
