```
solve_s_graphical_group(Σ::Symmetric, groups::Vector{Int}, group_reps::Vector{Int},
method; [m], [verbose])
```

Solves the group knockoff problem but the convex optimization problem only runs on the representatives. The non-representative variables are assumed to be  independent by groups when conditioning on the reprensetatives. 

# Inputs

  * `Σ`: Symmetric `p × p` covariance matrix
  * `groups`: `p` dimensional vector of group membership
  * `group_reps`: Indices for the representatives.
  * `method`: Method for solving group knockoff problem
  * `m`: Number of knockoffs to generate per feature
  * `verbose`: Whether to print informative intermediate results
  * `kwargs...`: extra arguments for [`solve_s_group`](@ref)

# Outputs

  * `S`: Matrix obtained from solving the optimization problem on the representatives.
  * `D`: A `p × p` (dense) matrix corresponding to the S matrix for both the   representative and non-representative variables. Knockoff sampling should    use this matrix. If the graphical conditional independent assumption is    satisfied exactly, this matrix should be sparse, but it is always never sparse   unless we use `cond_indep_corr` to force the covariance matrix to satisify it.
  * `obj`: Objective value for solving the optimization problem on the representatives.
