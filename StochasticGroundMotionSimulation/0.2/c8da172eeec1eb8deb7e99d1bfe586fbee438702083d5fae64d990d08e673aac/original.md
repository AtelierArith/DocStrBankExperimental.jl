```
fourier_spectrum(f::Vector{U}, m::S, r_ps::T, fas::FourierParameters) where {S<:Real,T<:Real,U<:Float64}
```

Fourier acceleration spectrum (m/s) based upon an equivalent point source distance `r_ps`

  * `f` is `Vector` of frequencies (Hz)
  * `m` is magnitude
  * `r_ps` is the equivalent point source distance including saturation effects (km)
  * `fas` are the Fourier spectral parameters `FourierParameters`

See also: [`fourier_spectral_ordinate`](@ref)
