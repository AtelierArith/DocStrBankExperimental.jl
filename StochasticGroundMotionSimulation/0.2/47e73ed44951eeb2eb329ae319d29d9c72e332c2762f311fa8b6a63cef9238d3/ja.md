```
fourier_spectral_ordinate(f::S, m::S, r_ps::T, src::SourceParameters, geo::GeometricSpreadingParameters, ane::AnelasticAttenuationParameters, site::SiteParameters) where {S<:Float64,T<:Real}
```

等価点源距離 `r_ps` に基づくフーリエ加速度スペクトルオルディネート (m/s)

  * `f` は周波数 (Hz)
  * `m` はマグニチュード
  * `r_ps` は飽和効果を含む等価点源距離 (km)
  * `src` はソースパラメータ `SourceParameters`
  * `geo` は幾何学的拡散パラメータ `GeometricSpreadingParameters`
  * `sat` は近接ソース飽和パラメータ `NearSourceSaturationParameters`
  * `ane` は非弾性減衰パラメータ `AnelasticAttenuationParameters`
  * `site` はサイトパラメータ `SiteParameters`

参照: [`fourier_spectrum`](@ref), [`fourier_spectrum!`](@ref)
