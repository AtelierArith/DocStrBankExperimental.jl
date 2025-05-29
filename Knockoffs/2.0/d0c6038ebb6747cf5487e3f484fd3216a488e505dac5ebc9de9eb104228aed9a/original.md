```
modelX_gaussian_group_knockoffs(X, method, groups, μ, Σ; [m], [covariance_approximator], [kwargs])
modelX_gaussian_group_knockoffs(X, method, groups; [m], [covariance_approximator], [kwargs])
```

Constructs Gaussian model-X group knockoffs. If the covariance `Σ` and mean `μ`  are not specified, they will be estimated from data, i.e. we will make second-order group knockoffs. To incorporate group structure, the (true or estimated) covariance  matrix is block-diagonalized according to `groups` membership to solve a relaxed  optimization problem. See reference paper and Knockoffs.jl docs for more details. 

# Inputs

  * `X`: A `n × p` design matrix. Each row is a sample, each column is a feature.
  * `method`: Method for constructing knockoffs. Options include

      * `:maxent`: (recommended) for fully general maximum entropy group knockoffs
      * `:mvr`: for fully general minimum variance-based reconstructability (MVR) group    knockoffs
      * `:equi`: for equi-correlated knockoffs. This is the methodology proposed in   `Dai R, Barber R. The knockoff filter for FDR control in group-sparse and multitask regression.    International conference on machine learning 2016 Jun 11 (pp. 1851-1859). PMLR.`
      * `:sdp`: Fully general SDP group knockoffs based on coodinate descent
      * `:sdp_block`: Fully general SDP group knockoffs where each block is solved exactly    using an interior point solver.
      * `:sdp_subopt`: Chooses each block `S_{i} = γ_i * Σ_{ii}`. This slightly    generalizes the equi-correlated group knockoff idea proposed in Dai and Barber 2016.
  * `groups`: Vector of group membership
  * `μ`: A length `p` vector storing the true column means of `X`
  * `Σ`: A `p × p` covariance matrix for columns of `X`
  * `m`: Number of knockoffs per variable, defaults to 1.
  * `covariance_approximator`: A covariance estimator, defaults to    `LinearShrinkage(DiagonalUnequalVariance(), :lw)`. See CovarianceEstimation.jl    for more options.
  * `kwargs`: Extra keyword arguments for `solve_s_group`

# How to define groups

The exported functions `hc_partition_groups` can be used to build a group  membership vector. 

# A note on compute time

The computational complexity of group knockoffs scales quadratically with group size. Thus, very large groups (e.g. >100 members per group) dramatically slows down  parameter estimation. In such cases, one can consider running the routine  `modelX_gaussian_rep_group_knockoffs` which constructs group knockoffs by choosing top representatives from each group. 

# Reference

Dai & Barber 2016, The knockoff filter for FDR control in group-sparse and multitask regression
