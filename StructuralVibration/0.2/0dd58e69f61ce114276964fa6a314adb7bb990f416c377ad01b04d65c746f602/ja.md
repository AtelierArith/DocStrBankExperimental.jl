```
SdofForcedTimeProblem(sdof, u0, t, F, ω, type_exc)
```

任意の励起を受けるsdofシステムの時間問題のデータを含む構造体

**フィールド**

  * `sdof::Sdof`: Sdof構造体
  * `F::AbstractVector`: 励起の振幅 [N] または基底の動き [m]
  * `u0::AbstractVector`: 初期条件

      * `x0`: 初期変位 [m]
      * `v0`: 初期速度 [m/s]
  * `t::AbstractRange`: 応答を評価する時間点
  * `type_exc::Symbol`: 励起の種類

      * `:force`: 外部力（デフォルト）
      * `:base`: 基底の動き
