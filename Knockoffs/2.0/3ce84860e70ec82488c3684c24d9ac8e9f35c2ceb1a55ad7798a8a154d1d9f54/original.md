```
fixed_knockoffs(X::Matrix{T}; [method], [kwargs...])
```

Creates fixed-X knockoffs. Internally, `X` will be automatically normalized before computing its knockoff. 

# Inputs

  * `X`: A column-normalized `n × p` numeric matrix, each row is a sample, and   each column is covariate. We will internally normalized `X` if it is not.
  * `method`: Can be one of the following

      * `:mvr`: Minimum variance-based reconstructability knockoffs (alg 1 in ref 2)
      * `:maxent`: Maximum entropy knockoffs (alg 2 in ref 2)
      * `:equi`: Equi-distant knockoffs (eq 2.3 in ref 1),
      * `:sdp`: SDP knockoffs (eq 2.4 in ref 1)
      * `:sdp_fast`: SDP knockoffs via coordiate descent (alg 2.2 in ref 3)
  * `kwargs...`: Possible optional inputs to `method`, see [`solve_MVR`](@ref),    [`solve_max_entropy`](@ref), and [`solve_sdp_ccd`](@ref)

# Output

  * `GaussianKnockoff`: A struct containing the original (column-normalized) `X`   and its knockoff `X̃`, in addition to other variables (e.g. `s`)

# Reference

1. "Controlling the false discovery rate via Knockoffs" by Barber and Candes (2015).
2. "Powerful knockoffs via minimizing reconstructability" by Spector, Asher, and Lucas Janson (2020)
3. "FANOK: Knockoffs in Linear Time" by Askari et al. (2020).
