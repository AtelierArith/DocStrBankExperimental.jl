```
fourier_spectrum!(Af::Vector{U}, f::Vector{V}, m::S, r_ps::T, fas::FourierParameters) where {S<:Real,T<:Real,U<:Real,V<:Float64}
```

等価点源距離 `r_ps` に基づくフーリエ加速度スペクトル (m/s)

  * `Af` は埋め込むフーリエ加速度スペクトルの振幅のベクトル (m/s)
  * `f` は周波数の `Vector` (Hz)
  * `m` は大きさ
  * `r_ps` は飽和効果を含む等価点源距離 (km)
  * `fas` はフーリエスペクトルパラメータ `FourierParameters`

参照: [`fourier_spectrum`](@ref)
