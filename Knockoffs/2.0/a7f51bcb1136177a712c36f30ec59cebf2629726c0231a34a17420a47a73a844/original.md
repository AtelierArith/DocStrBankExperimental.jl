```
solve_s(Σ::Symmetric, method::Symbol; m=1, kwargs...)
```

Solves the vector `s` for generating knockoffs. `Σ` can be a general  covariance matrix but it must be wrapped in the `Symmetric` keyword. 

# Inputs

  * `Σ`: A covariance matrix (one must wrap `Symmetric(Σ)` explicitly)
  * `method`: Can be one of the following

      * `:mvr` for minimum variance-based reconstructability knockoffs (alg 1 in ref 2)
      * `:maxent` for maximum entropy knockoffs (alg 2 in ref 2)
      * `:equi` for equi-distant knockoffs (eq 2.3 in ref 1),
      * `:sdp` for SDP knockoffs (eq 2.4 in ref 1)
      * `:sdp_ccd` fast SDP knockoffs via coordiate descent (alg 2.2 in ref 3)
  * `m`: Number of knockoffs per variable, defaults to 1.
  * `kwargs`: Extra arguments available for specific methods. For example, to use    less stringent convergence tolerance for MVR knockoffs, specify `tol = 0.001`.   For a list of available options, see [`solve_MVR`](@ref),   [`solve_max_entropy`](@ref), [`solve_sdp_ccd`](@ref), [`solve_SDP`](@ref), or   [`solve_equi`](@ref)

# Reference

1. "Controlling the false discovery rate via Knockoffs" by Barber and Candes (2015).
2. "Powerful knockoffs via minimizing reconstructability" by Spector, Asher, and Lucas Janson (2020)
3. "FANOK: Knockoffs in Linear Time" by Askari et al. (2020).
