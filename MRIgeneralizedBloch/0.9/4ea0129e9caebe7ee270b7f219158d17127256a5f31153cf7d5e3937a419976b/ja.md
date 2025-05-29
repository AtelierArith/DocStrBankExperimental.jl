```
graham_saturation_rate_single_frequency(lineshape, ω1, TRF, Δω)
```

グラハムの単一周波数近似に従って飽和率（単位は1/s）を計算します。

# 引数

  * `lineshape::Function`: ω₀（単位はrad/s）の関数として。例えば、匿名関数 `ω₀ -> lineshape_superlorentzian(ω₀, T2s)` を供給します。ラインシェイプの積分は1である必要があります。
  * `ω1::Function`: 時間（単位はs）に対するω1（単位はrad/s）で、パルス形状がt ∈ [0,TRF]の範囲で定義されています。
  * `TRF::Real`: RFパルスの持続時間（単位はs）
  * `Δω::Real`: オフセット周波数（単位はrad/s）

# 例

```jldoctest
julia> using SpecialFunctions

julia> T2s = 10e-6;

julia> α = π;

julia> TRF = 100e-6;

julia> NSideLobes = 1;

julia> ω1(t) = sinc(2(NSideLobes+1) * t/TRF - (NSideLobes+1)) * α / (sinint((NSideLobes+1)π) * TRF/π / (NSideLobes+1));

julia> Δω = 200;

julia> graham_saturation_rate_single_frequency(ω₀ -> lineshape_superlorentzian(ω₀, T2s), ω1, TRF, Δω)
419969.3376658947
```
