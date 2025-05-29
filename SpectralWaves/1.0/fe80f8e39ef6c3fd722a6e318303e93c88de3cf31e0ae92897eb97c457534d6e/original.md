```
solve_problem!(p::Problem; msg_flag = true)
```

Calculate solution coefficients `η̂`, `η̇`, `ϕ̂`, `ϕ̇`, `ψ̂`, `ψ̇` of the wave problem.

Modified in-place variables:

  * `η̂` are free-surface elevation potential amplitudes (m),
  * `η̇` are free-surface vertical velocity amplitudes (m/s),
  * `ϕ̂` are flat-bottom velocity potential amplitudes (m²/s),
  * `ϕ̇` are flat-bottom acceleration potential amplitudes (m²/s²),
  * `ψ̂` are uneven-bottom velocity potential amplitudes (m²/s),
  * `ψ̇` are uneven-bottom acceleration potential amplitudes (m²/s²),

Input variables:

  * `β̂` are bottom-surface elevation amplitudes (m),
  * `β̇` are bottom-surface vertical velocity amplitudes (m/s),
  * `p̂` are surface pressure head amplitudes (m),
  * `κ` are wave numbers (rad/m),
  * `𝒯` are hyperbolic tangent lookup values,
  * `𝒮` are hyperbolic secant lookup values,
  * `ℐ` is the number of harmonics,
  * `M_s` is the order of nonlinear free-surface boundary condition,
  * `M_b` is the order of nonlinear bottom boundary condition,
  * `Δt` is the time step (s),
  * `O` is the order of the time-stepping scheme,
  * `N` is the number of time steps,
  * `χ` is wavemaker paddle displacement (m),
  * `ξ` is wavemaker paddle velocity (m/s),
  * `ζ` is wavemaker paddle acceleration (m/s²),
  * `ℓ` is the fluid domain length (m),
  * `d` is the water depth (m).

Keyword arguments:

  * `static_bottom` is a boolean flag to indicate whether the bottom is static,
  * `msg_flag` is a boolean flag to indicate whether to print progress messages.
