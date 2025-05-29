```
SdofHarmonicTimeProblem(sdof, u0, t, F, ω, type_exc)
```

ハーモニック励起を受けるsdofシステムの時間問題のデータを含む構造体

**コンストラクタパラメータ**

  * `sdof::Sdof`: Sdof構造体
  * `F`: 力の励起の振幅 [N] または基底運動 [m]
  * `f`: 励起の周波数 [Hz]
  * `u0::AbstractVector`: 初期条件

      * `x0`: 初期変位 [m]
      * `v0`: 初期速度 [m/s]
  * `t::AbstractRange`: 応答を評価する時間点
  * `type_exc::Symbol`: 励起の種類

      * `:force`: 外部力（デフォルト）
      * `:base`: 基底運動

**フィールド**

  * `sdof::Sdof`: Sdof構造体
  * `F`: 力の励起の振幅 [N] または基底運動 [m]
  * `ω`: 励起の周波数 [rad/s]
  * `u0::AbstractVector`: 初期条件

      * `x0`: 初期変位 [m]
      * `v0`: 初期速度 [m/s]
  * `t::AbstractRange`: 応答を評価する時間点
  * `type_exc::Symbol`: 励起の種類

      * `:force`: 外部力（デフォルト）
      * `:base`: 基底運動
