```
graham_saturation_rate_spectral(lineshape, ω1, TRF, Δω)
```

グラハムのスペクトルモデルに従って飽和率（単位は 1/s）を計算します。

# 引数

  * `lineshape::Function`: ω₀（単位は rad/s）の関数として。例えば、匿名関数 `ω₀ -> lineshape_superlorentzian(ω₀, T2s)` を供給します。ラインシェイプの積分は1である必要があります。
  * `ω1::Function`: 時間（単位は s）に対する ω1（単位は rad/s）で、パルス形状が t ∈ [0,TRF] の範囲で定義されます。
  * `TRF::Real`: RFパルスの持続時間（単位は s）
  * `Δω::Real`: オフセット周波数（単位は rad/s）

# 例

```jldoctest
julia> using SpecialFunctions

julia> T2s = 10e-6;

julia> α = π;

julia> TRF = 100e-6;

julia> NSideLobes = 1;

julia> ω1(t) = sinc(2(NSideLobes+1) * t/TRF - (NSideLobes+1)) * α / (sinint((NSideLobes+1)π) * TRF/π / (NSideLobes+1));

julia> Δω = 200;

julia> graham_saturation_rate_spectral(ω₀ -> lineshape_superlorentzian(ω₀, T2s), ω1, TRF, Δω)
56135.388046022905
```
