```
mutable struct ActiveVirtualOscillator <: ActivePowerControl
    k1::Float64
    ψ::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

アクティブバーチャルオシレーターコントローラーのパラメータ。モデルは ["Model Reduction for Inverters with Current Limiting and Dispatchable Virtual Oscillator Control."](https://doi.org/10.1109/TEC.2021.3083488) に基づいています。

# 引数

  * `k1::Float64`: VOC同期ゲイン、検証範囲: `(0, nothing)`
  * `ψ::Float64`: コントローラーの回転角、検証範囲: `(0, nothing)`
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照電力セットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための [*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) ActiveVirtualOscillatorモデルの [states](@ref S) は次の通りです:

```
θ_oc: インバータモデルの位相角変位
```

  * `n_states::Int`: (**変更しないでください。**) ActiveVirtualOscillatorは1つの状態を持ちます。
