```
scan(y, G, K; optional inputs) 
scan(y, G, Z, K; optional inputs) - if modeling additional covariates Z
```

Perform genome scan for univariate trait and a set of genome markers

# Required Inputs

  * `y::Array{Float64, 2} or Array{Float64, 1}`: Single univariate quantitative trait of N measurements (dimension: N*1)
  * `G::Array{Float64, 2}`: Matrix of genotype probabilities at p tested markers (dimension: N*p)
  * `K::Array{Float64, 2}`: Genetic relatedness matrix of the N subjects (dimension:N*N)

# Optional Inputs

## Essential Inputs:

  * `addIntercept::Bool`: Option to add an intercept column to the design matrix (default: true)
  * `reml::Bool`: Option of the scheme for estimating variance components (by REML or ML; default: false)
  * `assumption::String`: Keyword argument indicating whether to estimate the variance components independently    for each marker ("alt") or to estimate once for the null model and use for testing all markers ("null)   (default: "null")
  * `output_pvals::Bool`: Option to additionally report the LRT p-values (default: false)

## Modeling Additional Covariates:

  * `Z::AbstractArray{Float64, 2}`: Matrix of additional non-genetic covariates (should be independent to tested    markers)

## Permutation Testing:

  * `permutation_test::Bool`: Option to perform permutation testing on the studied single trait (default: false)
  * `nperms::Int64`: The number of permutations required, an integer (default: 1024)
  * `rndseed::Int64`: An integer random seed set for performing random shuffling of the original trait    (default: 0)

## Structure of Weighted Residual Variances:

  * `weights::Array{Float64, 1}`: Optional weights for modeling unequal, weighted structure of the residual variances    of the trait (default: Missing, i.e. equal residual variances)

## Numerical Techniques - for stabilizing the heritability optimization step

  * `optim_interval::Int64`: The number of sub-divided regions of the interval [0, 1) of heritability to perform each    numerical optimization scheme (the Brent's method) on (default: 1, i.e. the entire interval)
  * `prior_variance::Float64`: Scale parameter of the prior Scaled Inv-Chisq distributed residual variances (default: 0)
  * `prior_sample_size::Float64`: Degree of freedom parameter of the prior Scaled Inv-Chisq distributed residual    variances (default: 0)

## Examining Profile Likelihood - as a function of the heritability estimates

  * `ProfileLL::Bool`: Option to return values of the profile likelihood function under different h2 values    (default: false)
  * `markerID::Int64`: The ID of the marker of interest
  * `h2_grid::Array{Float64, 1}`: Different values of h2 for calculating the corresponding profile likelihood values   (default: an empty array)

## Other Inputs:

  * `method::String`: Keyword indicating the matrix factorization scheme for model evaluation; either by "qr" or    "cholesky" decomposition (default: "qr")
  * `decomp_scheme::String`: Keyword indicating the decomposition scheme for the kinship matrix; either by "eigen"    or "svd" decomposition (default: "eigen")

# Returned Values:

The output of the single-trait scan function is an object. Depending on the user inputs and options, the fields of     the output object will differ. For example, for the returned output named as `out`:

## Null-LMM: by the "Null" approximation of the h2 value and applied to testing all markers:

  * `out.sigma2_e::Float64`: Estimated residual unexplained variances from the null model
  * `out.h2_null::Float64`: Estimated heritability (h2) from the null model
  * `out.lod::Array{Float64, 1}`: 1-dimensional array consisting of the LOD scores

## Exact-LMM: by re-estimating the h2 and sigma2_e independently while testing each marker:

  * `out.sigma2_e::Float64`: Estimated residual unexplained variances from the null model
  * `out.h2_null::Float64`: Estimated heritability (h2) from the null model
  * `out.h2_each_marker::Array{Float64, 1}`: 1-dimensional array of the estimated heritability for each marker model
  * `out.lod::Array{Float64, 1}`: 1-dimensional array consisting of the LOD scores

## Null-LMM and when permutation testing is required:

  * `out.sigma2_e::Float64`: Estimated residual unexplained variances from the null model
  * `out.h2_null::Float64`: Estimated heritability (h2) from the null model
  * `out.lod::Array{Float64, 1}`: 1-dimensional array consisting of the LOD scores
  * `out.L_perms::Array{Float64, 2}`: 2-dimensional array of the LOD scores from permutation testing; each column   is a vector of length p of p LOD scores for each permuted copy.

## If the option for reporting p-values is on, the p-values results will be returned as:

  * `out.log10pvals::Array{Float64, 1}`: 1-dimensional array consisting of the -log10(p-values)
  * `out.log10Pvals_perms::Array{Float64, 2}`: 2-dimensional array consisting of the -log10(p-values) for each test

(for testing the association between each marker and each permuted trait).

## Additionally, if the user wants to examine the profile likelihood values under a given set of h2-values:

  * `out.ll_list_null::Array{Float64, 1}`: gives the values under the null model under each h2-value
  * `out.ll_list_alt::Array{Float64, 1}`: gives the values under the user-specified marker model under each h2-value
