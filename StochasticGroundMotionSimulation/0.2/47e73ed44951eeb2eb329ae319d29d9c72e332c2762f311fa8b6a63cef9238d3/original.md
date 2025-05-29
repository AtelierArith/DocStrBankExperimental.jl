```
fourier_spectral_ordinate(f::S, m::S, r_ps::T, src::SourceParameters, geo::GeometricSpreadingParameters, ane::AnelasticAttenuationParameters, site::SiteParameters) where {S<:Float64,T<:Real}
```

Fourier acceleration spectral ordinate (m/s) based upon an equivalent point source distance `r_ps`

  * `f` is frequency (Hz)
  * `m` is magnitude
  * `r_ps` is the equivalent point source distance including saturation effects (km)
  * `src` are the source parameters `SourceParameters`
  * `geo` are the geometric spreading parameters `GeometricSpreadingParameters`
  * `sat` are the near source saturation parameters `NearSourceSaturationParameters`
  * `ane` are the anelastic attenuation parameters `AnelasticAttenuationParameters`
  * `site` are the site parameters `SiteParameters`

See also: [`fourier_spectrum`](@ref), [`fourier_spectrum!`](@ref)
