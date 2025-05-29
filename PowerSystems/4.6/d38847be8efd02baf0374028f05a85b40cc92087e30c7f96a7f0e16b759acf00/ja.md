```
mutable struct KauraPLL <: FrequencyEstimator
    ω_lp::Float64
    kp_pll::Float64
    ki_pll::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

位相同期ループ（PLL）のパラメータは、Vikram Kaura と Vladimir Blasko による ["Operation of a phase locked loop system under distorted utility conditions"](https://doi.org/10.1109/28.567077) に基づいています。

# 引数

  * `ω_lp::Float64`: PLL ローパスフィルタ周波数 (rad/sec)、検証範囲: `(0, nothing)`
  * `kp_pll::Float64`: PLL 比例ゲイン、検証範囲: `(0, nothing)`
  * `ki_pll::Float64`: PLL 積分ゲイン、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための [*ext*ra 辞書](@ref additional_fields) で、緯度や経度などが含まれます。
  * `states::Vector{Symbol}`: (**変更しないでください。**) KauraPLL モデルの [states](@ref S) は次のとおりです：

```
vd_pll: PLL 同期参照フレーム (SRF) における測定電圧の d 軸、
vq_pll: PLL SRF における測定電圧の q 軸、
ε_pll: PI コントローラの積分器状態、
θ_pll: PLL SRF における位相角の変位
```

  * `n_states::Int`: (**変更しないでください。**) KauraPLL には 4 つの状態があります。
