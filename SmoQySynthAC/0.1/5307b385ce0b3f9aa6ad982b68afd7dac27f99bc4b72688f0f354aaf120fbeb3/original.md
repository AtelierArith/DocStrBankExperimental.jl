```
spectral_to_matsubara_correlation_function(;
    # KEYWORD ARGUMENTS
    n::AbstractVector{Int},
    β::T,
    spectral_function::Function,
    kernel_function::Function,
    tol::T = 1e-10,
    bounds = (-Inf, 0.0, +Inf),
    normalize::Bool = false
) where {T<:AbstractFloat}
```

Calculate and return the Matsubara correlation function

$$
C({\rm i} \omega_n) = \int_{-\infty}^{\infty} d\omega \ K_\beta(\omega, \omega_n) \ A(\omega).
$$

for a vector of $n \in \mathbb{Z}$ values, given a spectral function $A(\omega)$ (`spectral_function`) and kernel function $K_\beta(\omega,\omega_n)$ (`kernel_function`). This integral is evaluated within a specified tolerance `tol`.

Note that the kernel function should be called as `kernel_function(ω, n, β)` where `n` specifies the Matsubara frequency, which is evaluated internally as either $\omega_n = (2n+1)\pi/\beta$ or $\omega_n = 2n\pi/\beta$ depending on whether the kernel function is fermionic of bosonic respectively.

## Arguments

  * `n::AbstractVector{Int}`: Vector of integers specifying Matsubara frequencies for which $C({\rm i}\omega_n)$ will be evaluated.
  * `spectral_function::Function`: The spectral function $A(\omega)$ that takes a single argument.
  * `kernel_function::Function`: The kernel function $K_\beta(\omega,\omega_n)$ that takes three arguments as shown.
  * `tol::T = 1e-10`: Specified precision with which $C({\rm i}\omega_n)$ is evaluated.
  * `bounds = (-Inf, +Inf)`: Bounds on integration domain.
  * `normalize::Bool = false`: Whether the spectral function needs to be normalized to unity.
