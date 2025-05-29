```
modelX_gaussian_knockoffs(X::Matrix, method::Symbol; [m], [covariance_approximator], [kwargs...])
modelX_gaussian_knockoffs(X::Matrix, method::Symbol, μ::Vector, Σ::Matrix; [m], [kwargs...])
```

Creates model-free multivariate normal knockoffs by sequentially sampling from  conditional multivariate normal distributions. The true mean `μ` and covariance `Σ` is estimated from data if not supplied. 

# Inputs

  * `X`: A `n × p` numeric matrix, each row is a sample, and each column is covariate.
  * `method`: Can be one of the following

      * `:mvr` for minimum variance-based reconstructability knockoffs (alg 1 in ref 2)
      * `:maxent` for maximum entropy knockoffs (alg 2 in ref 2)
      * `:equi` for equi-distant knockoffs (eq 2.3 in ref 1),
      * `:sdp` for SDP knockoffs (eq 2.4 in ref 1)
      * `:sdp_ccd` for SDP knockoffs via coordiate descent (alg 2.2 in ref 3)
  * `μ`: A `p × 1` vector of column mean of `X`, defaults to column mean
  * `Σ`: A `p × p` matrix of covariance of `X`, defaults to a shrinkage estimator   specified by `covariance_approximator`.
  * `m`: Number of knockoff copies per variable to generate, defaults to 1.
  * `covariance_approximator`: A covariance estimator, defaults to `LinearShrinkage(DiagonalUnequalVariance(), :lw)`   which tends to give good empirical performance when p>n. See CovarianceEstimation.jl for more options.
  * `kwargs...`: Possible optional inputs to solvers specified in `method`, see    [`solve_MVR`](@ref), [`solve_max_entropy`](@ref), and [`solve_sdp_ccd`](@ref)

# Reference:

1. "Panning for Gold: Model-X Knockoffs for High-dimensional Controlled  Variable Selection" by Candes, Fan, Janson, and Lv (2018)
2. "Powerful knockoffs via minimizing reconstructability" by Spector, Asher, and Lucas Janson (2020)
3. "FANOK: Knockoffs in Linear Time" by Askari et al. (2020).

# Covariance Approximation:

The covariance is approximated by a linear shrinkage estimator using  Ledoit-Wolf with `DiagonalUnequalVariance` target,  which seems to perform well for `p>n` cases. We do not simply use `cov(X)` since `isposdef(cov(X))` is typically false. For comparison of various estimators, see: https://mateuszbaran.github.io/CovarianceEstimation.jl/dev/man/msecomp/#msecomp
