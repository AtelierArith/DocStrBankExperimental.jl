```
ColoredNoise(F, color)
```

カラー雑音励起信号を定義する構造体

**フィールド**

  * `F::Real`: 力の平均振幅 [N]
  * `tstart::Real`: 励起の開始時間 [s]
  * `duration::Real`: 励起の持続時間 [s]
  * `σ::Real`: カラー雑音の目標標準偏差
  * `color::Symbol`: 雑音の色

      * `:white` (デフォルト)
      * `:pink`
      * `:blue`
      * `:brown`
      * `:purple`
  * `band_freq::AbstractVector`: カラー雑音に適用されるバンドパスフィルターを定義するために使用される周波数
