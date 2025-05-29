```
grad_smooth_qp_green(x, params::NamedTuple, grad::NamedTuple, Yε_cache::IntegrationCache; nb_terms=50)
```

Compute the first order derivative of the smooth α-quasi-periodic Green's function using the FFT-based method [Zhang2018](@cite) with series expansion fallback.

# Input arguments

  * `x`: 2D point at which to evaluate the Green's function.
  * `params`: Physical and numerical parameters containing:

      * `alpha`: Quasiperiodicity coefficient
      * `k`: Wavenumber
      * `c`: Lower cutoff parameter for function `χ`.
      * `c_tilde`: Upper cutoff parameter for function `χ`.
      * `epsilon`: cutoff parameter for function `Yε` (recommended: `0.4341`).
      * `order`: Quadrature order
  * `grad`: Bicubic spline interpolator for the gradient of `Ln`.
  * `Yε_cache`: Precomputed cache for cutoff function `Yε` evaluations.

# Keyword Arguments

  * `nb_terms`: Number of terms to use in the eigenfunction expansion fallback (when `x₂ ∉ [-c, c]`)

# Returns

  * `∇G_0`: The approximate value of the fist order derivative of the smooth quasiperiodic Green's function at point `x`
