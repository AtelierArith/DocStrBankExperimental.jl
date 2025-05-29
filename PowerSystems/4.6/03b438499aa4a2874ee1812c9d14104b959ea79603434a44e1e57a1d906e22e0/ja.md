```
mutable struct HybridOutputCurrentLimiter <: OutputCurrentLimiter
    I_max::Float64
    rv::Float64
    lv::Float64
    ext::Dict{String, Any}
end
```

ハイブリッド電流制御器リミッターのパラメータ。インバータ出力電流の大きさを調整しますが、仮想インピーダンスによって調整された閉ループフィードバックによりアンチウィンドアップを提供します。記載されている文献: Novel Hybrid Current Limiter for Grid-Forming Inverter Control During Unbalanced Faults by Baeckland and Seo, 2023 

# 引数

  * `I_max::Float64`: 電流制御器入力電流の最大制限（デバイスベース）、検証範囲: `(0, nothing)`
  * `rv::Float64`: 仮想インピーダンスの実部、検証範囲: `(0, nothing)`
  * `lv::Float64`: 仮想インピーダンスの虚部、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`)
