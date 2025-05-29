```
solve_SDP(Σ::AbstractMatrix)
```

Solves the SDP problem for fixed-X and model-X knockoffs given correlation matrix Σ.  Users should call `solve_s` instead of this function. 

The optimization problem is stated in equation 3.13 of https://arxiv.org/pdf/1610.02351.pdf

# Arguments

  * `Σ`: A correlation matrix (diagonals all equal to 1)
  * `m`: Number of knockoffs to generate, defaults to 1
  * `optm`: SDP solver. Defaults to `Hypatia.Optimizer(verbose=false)`. This can   be any solver that supports the JuMP interface. For example, use    `SDPT3.Optimizer` in SDPT3.jl package (which is a MATLAB dependency)   for the best performance.
