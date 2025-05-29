```
fourier_spectral_ordinate(f::U, m::S, r_ps::T, src::SourceParameters, path::PathParameters, site::SiteParameters) where {S<:Real,T<:Real,U<:Float64}
```

Fourier acceleration spectral ordinate (m/s) based upon an equivalent point source distance `r_ps`

  * `f` is frequency (Hz)
  * `m` is magnitude
  * `r_ps` is the equivalent point source distance including saturation effects (km)
  * `src` are the source parameters `SourceParameters`
  * `path` are the path parameters `PathParameters`
  * `site` are the site parameters `SiteParameters`
