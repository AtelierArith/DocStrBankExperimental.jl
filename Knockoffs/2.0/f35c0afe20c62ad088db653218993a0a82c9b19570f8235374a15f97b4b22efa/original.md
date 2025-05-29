```
solve_s_group(Σ, groups, method; [m=1], kwargs...)
```

Solves the group knockoff problem, returns block diagonal matrix S satisfying `(m+1)/m*Σ - S ⪰ 0` where `m` is number of knockoffs per feature. 

# Inputs

  * `Σ`: A general covariance matrix wrapped by `Symmetric` keyword
  * `groups`: Vector of group membership, does not need to be contiguous
  * `method`: Method for constructing knockoffs. Options include

      * `:maxent`: (recommended) for fully general maximum entropy group knockoffs
      * `:mvr`: for fully general minimum variance-based reconstructability (MVR) group    knockoffs
      * `:equi`: for equi-correlated knockoffs. This is the methodology proposed in   `Dai R, Barber R. The knockoff filter for FDR control in group-sparse and multitask regression.    International conference on machine learning 2016 Jun 11 (pp. 1851-1859). PMLR.`
      * `:sdp`: Fully general SDP group knockoffs based on coodinate descent
      * `:sdp_subopt`: Chooses each block `S_{i} = γ_i * Σ_{ii}`. This slightly    generalizes the equi-correlated group knockoff idea proposed in Dai and Barber 2016.
      * `:sdp_block`: Fully general SDP group knockoffs where each block is solved exactly    using an interior point solver.
  * `m`: Number of knockoffs per variable, defaults to 1.
  * `kwargs`: Extra arguments available for specific methods. For example, to use    less stringent convergence tolerance, specify `tol = 0.001`.   For a list of available options, see [`solve_group_mvr_hybrid`](@ref),   [`solve_group_max_entropy_hybrid`](@ref), [`solve_group_sdp_hybrid`](@ref), or   [`solve_group_equi`](@ref)

# Output

  * `S`: A matrix solved so that `(m+1)/m*Σ - S ⪰ 0` and `S ⪰ 0`
  * `γ`: A vector that is only non-empty for equi and suboptimal knockoff constructions.    They correspond to values of γ where `S_{gg} = γΣ_{gg}`. So for equi, the   vector is length 1. For SDP, the vector has length equal to number of groups
  * `obj`: Final SDP/MVR/ME objective value given `S`. Equi-correlated group knockoffs   and singleton (non-grouped knockoffs) returns 0 because they either no objective    value or it is not necessary to evaluate the objectives

# Warning

This function potentially permutes the columns/rows of `Σ`, and puts them back at the end. Thus one should NOT call `solve_s_group` on the same `Σ` simultaneously, e.g. in a multithreaded for loop. Permutation does not happen when groups are contiguous. 
