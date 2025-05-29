```
fourier_spectral_ordinate(f::U, m::S, r_ps::T, fas::FourierParameters) where {S<:Real,T<:Real,U<:Float64}
```

等価点源距離 `r_ps` に基づくフーリエ加速度スペクトルオルディネート (m/s)

  * `f` は周波数 (Hz)
  * `m` は大きさ
  * `r_ps` は飽和効果を含む等価点源距離 (km)
  * `fas` はフーリエスペクトルパラメータ `FourierParameters`
