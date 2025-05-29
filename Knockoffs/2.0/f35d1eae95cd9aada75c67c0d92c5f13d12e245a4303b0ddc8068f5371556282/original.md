```
approx_modelX_gaussian_knockoffs(X, method; [m=1], [windowsize = 500], [covariance_approximator], kwargs...)
approx_modelX_gaussian_knockoffs(X, method, window_ranges; [m=1], [covariance_approximator], kwargs...)
```

Generates Gaussian knockoffs by approximating the covariance as a block diagonal matrix.  Each block contains `windowsize` consecutive features. One could alternatively  specify the `window_ranges` argument to construct blocks of different sizes. 

# Inputs

  * `X`: A `n × p` numeric matrix or `SnpArray`. Each row is a sample, and each column is covariate.
  * `method`: Can be one of the following

      * `:mvr` for minimum variance-based reconstructability knockoffs (alg 1 in ref 2)
      * `:maxent` for maximum entropy knockoffs (alg 2 in ref 2)
      * `:equi` for equi-distant knockoffs (eq 2.3 in ref 1),
      * `:sdp` for SDP knockoffs (eq 2.4 in ref 1)
      * `:sdp_fast` for SDP knockoffs via coordiate descent (alg 2.2 in ref 3)
  * `m`: Number of knockoff copies per variable to generate, defaults to 1.
  * `windowsize`: Number of covariates to be included in a block. Each block consists of   adjacent variables. The last block could contain less than `windowsize` variables.
  * `window_ranges`: Vector of ranges for each window. e.g. [1:97, 98:200, 201:500]
  * `covariance_approximator`: A covariance estimator, defaults to `LinearShrinkage(DiagonalUnequalVariance(), :lw)`.   See CovarianceEstimation.jl for more options.
  * `kwargs...`: Possible optional inputs to solvers specified in `method`, see    [`solve_MVR`](@ref), [`solve_max_entropy`](@ref), and [`solve_sdp_ccd`](@ref)

# Multithreading (todo)

To enable multiple threads, simply start Julia with >1 threads and this routine will run with all available threads. 

# Covariance Approximation:

The covariance is approximated by a `LinearShrinkageEstimator` using  Ledoit-Wolf shrinkage with `DiagonalUnequalVariance` target,  which seems to perform well for `p>n` cases. We do not simply use `cov(X)` since `isposdef(cov(X))` is typically false. For comparison of different estimators, see: https://mateuszbaran.github.io/CovarianceEstimation.jl/dev/man/msecomp/#msecomp
