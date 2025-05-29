```
spectral_to_imaginary_time_correlation_function(;
    # KEYWORD ARGUMENTS
    τ::AbstractVector{T},
    β::T,
    spectral_function::Function,
    kernel_function::Function,
    tol::T = 1e-10,
    bounds = (-Inf, +Inf),
    normalize::Bool = false
) where {T<:AbstractFloat}
```

Calculate and return the imaginary-time correlation function

$$
C(\tau) = \int_{-\infty}^{\infty} d\omega \ K_\beta(\omega, \tau) \ A(\omega).
$$

on a grid of $\tau$ (`τ`) values, given a spectral function $A(\omega)$ (`spectral_function`) and kernel function $K_\beta(\omega,\tau)$ (`kernel_function`). This integral is evaluated within a specified tolerance `tol`.

## Arguments

  * `τ::AbstractVector{T}`: Vector of imaginary time such that `τ[end] = β` equal the inverse temperature.
  * `spectral_function::Function`: The spectral function $A(\omega)$ that takes a single argument.
  * `kernel_function::Function`: The kernel function $K_\beta(\omega,\tau)$ that takes three arguments as shown.
  * `tol::T = 1e-10`: Specified precision with which $C(\tau)$ is evaluated
  * `bounds = (-Inf, +Inf)`: Bounds on integration domain.
  * `normalize::Bool = false`: Whether the spectral function needs to be normalized to unity.
