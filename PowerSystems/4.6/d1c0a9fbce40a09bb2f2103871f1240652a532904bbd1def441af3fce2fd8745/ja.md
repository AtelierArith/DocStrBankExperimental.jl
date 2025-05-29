```
mutable struct ReducedOrderPLL <: FrequencyEstimator
    ω_lp::Float64
    kp_pll::Float64
    ki_pll::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

位相同期ループ（PLL）のパラメータに基づく ["Reduced-order Structure-preserving Model for Parallel-connected Three-phase Grid-tied Inverters."](https://doi.org/10.1109/COMPEL.2017.8013389)

# 引数

  * `ω_lp::Float64`: PLLローパスフィルタ周波数（ラジアン/秒）、検証範囲: `(0, nothing)`
  * `kp_pll::Float64`: PLL比例ゲイン、検証範囲: `(0, nothing)`
  * `ki_pll::Float64`: PLL積分ゲイン、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) ReducedOrderPLLモデルの[状態](@ref S)は次のとおりです：

```
vq_pll: PLL同期参照フレーム（SRF）における測定電圧のq軸、
ε_pll: PIコントローラの積分器状態、
θ_pll: PLL SRFにおける位相角の変位
```

  * `n_states::Int`: (**変更しないでください。**) ReducedOrderPLLは3つの状態を持ちます
