```
Problem(ℓ::Real, d::Real, ℐ::Integer, t::AbstractRange{Real}; O = 4, M_s = 0, M_b = 0, static_bottom = true)
```

Construct an IBV Problem object corresponding to a fluid domain of length `ℓ` and depth `d` with `ℐ` harmonics and `N` time steps.

Output is a Problem object with fields:

  * `ℓ` is the fluid domain length (m),
  * `d` is the water depth (m),
  * `ℐ` is the number of harmonics,
  * `t` is the time range,
  * `Δt` is the time step (s),
  * `N` is the number of time steps,
  * `O` is the order of the time-stepping scheme,
  * `κ` are wave numbers (rad/m),
  * `η̂` are free-surface elevation amplitudes (m),
  * `η̇` are free-surface vertical velocity amplitudes (m/s),
  * `β̂` are bottom-surface elevation amplitudes (m),
  * `β̇` are bottom-surface vertical velocity amplitudes (m/s),
  * `ϕ̂` are flat-bottom velocity potential amplitudes (m²/s),
  * `ϕ̇` are flat-bottom acceleration potential amplitudes (m²/s²),
  * `ψ̂` are uneven-bottom velocity potential amplitudes (m²/s),
  * `ψ̇` are uneven-bottom acceleration potential amplitudes (m²/s²),
  * `p̂` are surface pressure head amplitudes (m),
  * `χ` is wavemaker paddle displacement (m),
  * `ξ` is wavemaker paddle velocity (m/s),
  * `ζ` is wavemaker paddle acceleration (m/s²),
  * `𝒯` are hyperbolic tangent lookup values,
  * `𝒮` are hyperbolic secant lookup values,
  * `static_bottom` is a boolean flag to indicate if the bottom is static.
