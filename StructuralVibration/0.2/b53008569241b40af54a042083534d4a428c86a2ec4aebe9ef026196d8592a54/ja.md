```
SdofFRFProblem(sdof, freq, type_exc, type_resp)
```

FRFを計算するためのデータを含む構造体 sdof システム

**フィールド**

  * `sdof::Sdof`: Sdof 構造体
  * `freq::AbstractRange`: 周波数のベクトル [Hz]
  * `type_exc::Symbol`: 励起の種類

      * `:force`: 外部力 (デフォルト)
      * `:base`: 基底運動
  * `type_resp::Symbol`: 応答の種類

      * `:dis`: アドミタンス (デフォルト)
      * `:vel`: モビリティ
      * `:acc`: 加速度
