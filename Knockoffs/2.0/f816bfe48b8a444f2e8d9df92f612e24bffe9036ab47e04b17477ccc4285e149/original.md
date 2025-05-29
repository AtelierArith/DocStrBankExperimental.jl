```
modelX_gaussian_rep_group_knockoffs(X, method, groups; [m], [covariance_approximator], [kwargs...])
modelX_gaussian_rep_group_knockoffs(X, method, groups, μ, Σ; [m], [kwargs...])
```

Constructs group knockoffs by choosing representatives from each group and solving a smaller optimization problem based on the representatives only. Remaining knockoffs are generated based on a conditional independence assumption similar to a graphical model (details to be given later). The representatives are computed by [`choose_group_reps`](@ref)

# Inputs

  * `X`: A `n × p` design matrix. Each row is a sample, each column is a feature.
  * `method`: Method for constructing knockoffs. Options are the same as    `modelX_gaussian_group_knockoffs`
  * `groups`: Vector of `Int` denoting group membership. `groups[i]` is the group    of `X[:, i]`
  * `covariance_approximator`: A covariance estimator, defaults to    `LinearShrinkage(DiagonalUnequalVariance(), :lw)`. See CovarianceEstimation.jl    for more options.
  * `μ`: A length `p` vector storing the true column means of `X`
  * `Σ`: A `p × p` covariance matrix for columns of `X`
  * `rep_threshold`: Value between 0 and 1 that controls the number of    representatives per group. Larger means more representatives (default 0.5)
  * `m`: Number of knockoffs per variable, defaults to 1.
  * `kwargs`: Extra keyword arguments for `solve_s_group`
