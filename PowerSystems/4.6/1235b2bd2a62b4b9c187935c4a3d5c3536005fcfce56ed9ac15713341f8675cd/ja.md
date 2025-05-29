```
mutable struct SaturationOutputCurrentLimiter <: OutputCurrentLimiter
    I_max::Float64
    kw::Float64
    ext::Dict{String, Any}
end
```

サチュレーション電流制御器リミッタのパラメータ。インバータ出力電流の大きさを調整し、静的ゲインによって調整された閉ループフィードバックを適用し、アンチワインドアップを提供します。

# 引数

  * `I_max::Float64`: 電流制御器入力電流の最大制限（デバイスベース）、検証範囲: `(0, nothing)`
  * `kw::Float64`: 定義されたフィードバックゲイン、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`)
