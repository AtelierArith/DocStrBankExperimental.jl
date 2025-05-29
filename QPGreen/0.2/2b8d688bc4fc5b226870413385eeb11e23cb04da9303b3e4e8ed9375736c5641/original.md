```
init_qp_green_fft(params::NamedTuple, grid_size::Integer; derivative=false)
```

Preparation step of the FFT-based algorithm.

# Input arguments

  * `params`: Physical and numerical parameters, containing:

      * `alpha`: Quasiperiodicity coefficient.
      * `k`: Wave number.
      * `c`: Lower cutoff parameter for function χ.
      * `c_tilde`: Upper cutoff parameter for function χ.
      * `epsilon`: cutoff parameter for function Yε (recommended: `0.4341`).
      * `order`: Quadrature order for integration.
  * `grid_size`: Number of grid points per dimension (grid is `2 * grid_size × 2 * grid_size`).

# Keyword Arguments

  * `derivative`: if `true`, computes additionally the first-order derivative (`∇G`) of the quasi periodic Green's function.

# Returns

```
- If `derivative=false`: a NamedTuple with fields
        + `value`: Spline interpolator for the function `Ln`.
        + `cache`: Precomputed integration cache for reuse in later computations.
- If `derivative=true`: a NamedTuple with fields
        + `value`: Spline interpolator for the function `Ln`.
        + `grad`: Tuple of spline interpolators for the first derivatives of `Ln` (`∂/∂x₁`, `∂/∂x₂`).
        + `cache`: Precomputed integration cache for reuse in later computations.
```
