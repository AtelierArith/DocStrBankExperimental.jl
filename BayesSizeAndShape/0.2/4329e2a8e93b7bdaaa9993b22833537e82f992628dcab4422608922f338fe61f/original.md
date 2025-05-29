```
SizeAndShapeWithReflectionMCMC(
    landmarks::Array{Float64,3}, 
    fm::FormulaTerm,
    covariates::DataFrame, 
    iterations::NamedTuple{(:iter, :burnin, :thin),Tuple{Int64,Int64,Int64}},
    betaprior::ContinuousUnivariateDistribution,
    sigmaprior::ContinuousMatrixDistribution
)
```

Posterior samples from the size-and-shape model - in this version, only two-dimensional data with reflection information are allowed. 
The functions returns an object of type  `SizeAndShapeModelOutput`.

# Arguments

Let 

  * `n` be the number of objects;
  * `k+1` be the number of recorded landmark for each object
  * `p` be the dimension of each landmark (only p=2 or p=3)

The arguments of the functions are 

  * `landmarks`: a three-dimensional  `Array` of dimension $(k+1)\times p \times n$  with the data;
  * `fm`:  a `formula`, where on the left-hand side there must be 1 and on the right-hand side there is the actual regressive formula - an intercept is needed;
  * `covariates`: a `DataFrame` of covariates. The formula `fm` search for the covariates in the `DataFrame` column names;
  * `iterations`: a `NamedTuple` with `iter`, `burnin`, and `thin` values of the MCMC algorithm
  * `betaprior`:  a `Normal` distribution that is used as prior for all regressive coefficients
  * `sigmaprior`: an `InverseWishart` distribution that is used as prior for the covariance matrix.
