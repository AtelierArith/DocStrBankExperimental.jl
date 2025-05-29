```
mutable struct ReactiveVirtualOscillator <: ReactivePowerControl
    k2::Float64
    V_ref::Float64
    Q_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

リアクティブバーチャルオシレーターコントローラーのパラメータ。モデルは ["Model Reduction for Inverters with Current Limiting and Dispatchable Virtual Oscillator Control."](https://doi.org/10.1109/TEC.2021.3083488) に基づいています。

# 引数

  * `k2::Float64`: VOC電圧振幅制御ゲイン、検証範囲: `(0, nothing)`
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧セットポイント (pu)、検証範囲: `(0, nothing)`
  * `Q_ref::Float64`: (デフォルト: `1.0`) 参照リアクティブパワーセットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための [*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) リアクティブバーチャルオシレーターモデルの [states](@ref S) は次の通りです：

```
E_oc: d軸内制御のための電圧参照状態
```

  * `n_states::Int`: (**変更しないでください。**) リアクティブバーチャルオシレーターは1つの状態を持ちます。
