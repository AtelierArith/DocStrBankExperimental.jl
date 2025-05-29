```
fourier_spectrum!(Af::Vector{U}, f::Vector{V}, m::S, r_ps::T, fas::FourierParameters) where {S<:Real,T<:Real,U<:Real,V<:Float64}
```

Fourier acceleration spectrum (m/s) based upon an equivalent point source distance `r_ps`

  * `Af` is the vector of fas amplitudes to be filled (m/s)
  * `f` is `Vector` of frequencies (Hz)
  * `m` is magnitude
  * `r_ps` is the equivalent point source distance including saturation effects (km)
  * `fas` are the Fourier spectral parameters `FourierParameters`

See also: [`fourier_spectrum`](@ref)
