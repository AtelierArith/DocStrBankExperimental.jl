```
fourier_spectral_ordinate(f::U, m::S, r_ps::T, src::SourceParameters, path::PathParameters, site::SiteParameters) where {S<:Real,T<:Real,U<:Float64}
```

等価点源距離 `r_ps` に基づくフーリエ加速度スペクトルオルディネート (m/s)

  * `f` は周波数 (Hz)
  * `m` はマグニチュード
  * `r_ps` は飽和効果を含む等価点源距離 (km)
  * `src` はソースパラメータ `SourceParameters`
  * `path` はパスパラメータ `PathParameters`
  * `site` はサイトパラメータ `SiteParameters`
