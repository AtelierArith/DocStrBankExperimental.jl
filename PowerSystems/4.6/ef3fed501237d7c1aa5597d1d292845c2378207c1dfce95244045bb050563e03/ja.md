```
mutable struct VoltageModeControl <: InnerControl
    kpv::Float64
    kiv::Float64
    kffv::Float64
    rv::Float64
    lv::Float64
    kpc::Float64
    kic::Float64
    kffi::Float64
    ωad::Float64
    kad::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

仮想インピーダンスに基づく内部ループ電流制御PIDのパラメータは、["A Virtual Synchronous Machine implementation for distributed control of power converters in SmartGrids."](https://doi.org/10.1016/j.epsr.2015.01.001)に基づいています。

# 引数

  * `kpv::Float64`: 電圧制御器の比例ゲイン、検証範囲: `(0, nothing)`
  * `kiv::Float64`: 電圧制御器の積分ゲイン、検証範囲: `(0, nothing)`
  * `kffv::Float64`: 電圧のフィードフォワードゲインを有効にするためのバイナリ変数、検証範囲: `(0, nothing)`
  * `rv::Float64`: 仮想抵抗、検証範囲: `(0, nothing)`
  * `lv::Float64`: 仮想インダクタンス、検証範囲: `(0, nothing)`
  * `kpc::Float64`: 電流制御器の比例ゲイン、検証範囲: `(0, nothing)`
  * `kic::Float64`: 電流制御器の積分ゲイン、検証範囲: `(0, nothing)`
  * `kffi::Float64`: 電流のフィードフォワードゲインを有効にするためのバイナリ変数、検証範囲: `(0, nothing)`
  * `ωad::Float64`: アクティブダンピングフィルタのカットオフ周波数 (rad/sec)、検証範囲: `(0, nothing)`
  * `kad::Float64`: アクティブダンピングゲイン、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `states::Vector{Symbol}`: (**変更しないでください。**) VoltageModeControlモデルの[状態](@ref S)は次のとおりです：

```
ξd_ic: PI電圧制御器のd軸積分器状態、
ξq_ic: PI電圧制御器のq軸積分器状態、
γd_ic: PI電流制御器のd軸積分器状態、
γq_ic: PI電流制御器のq軸積分器状態、
ϕd_ic: アクティブダンピングのd軸ローパスフィルタ、
ϕq_ic: アクティブダンピングのq軸ローパスフィルタ
```

  * `n_states::Int`: (**変更しないでください。**) VoltageModeControlは6つの状態を持ちます
