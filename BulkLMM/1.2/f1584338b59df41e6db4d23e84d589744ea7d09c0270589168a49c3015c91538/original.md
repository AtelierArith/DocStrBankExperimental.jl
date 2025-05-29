bulkscan(Y, G, K; optional inputs) bulkscan(Y, G, Z, K; optional inputs) - if modeling additional covariates Z

Perform genome scan for multiple univariate traits and a set of genome markers

# Required Inputs

  * `Y::Array{Float64, 2}`: Matrix of multiple (m) traits; each column is a trait (dimension: N*m)
  * `G::Array{Float64, 2}`: Matrix of genotype probabilities at p tested markers (dimension: N*p)
  * `K::Array{Float64, 2}`: Genetic relatedness matrix of the N subjects (dimension:N*N)

# Optional Inputs

## Essential Inputs:

  * `addIntercept::Bool`: Option to add an intercept column to the design matrix (default: true)
  * `reml::Bool`: Option of the scheme for estimating variance components (by REML or ML; default: false)
  * `method::String`: Keyword argument indicating which multi-trait scan method will be used; currently supported    options: "null-grid" (fastest, grid-search approximated Null-LMM), "null-exact" (Null-LMM), and "alt-grid"    (grid-search approximated Exact-LMM)
  * `output_pvals::Bool`: Option to additionally report the LRT p-values (default: false)

## Modeling Additional Covariates:

  * `Z::AbstractArray{Float64, 2}`: Matrix of additional non-genetic covariates (should be independent to tested    markers)

## Different Optional Inputs by the Method Chosen:

```
For the multiple-trait scans, the user may choose to apply one of the three methods, depending on
the need for gaining more precision or waiting for shorter time. The allowed inputs differ by the choice:
```

### Grid-search approximation method: "null-grid" (default method) and "alt-grid"

  * `h2_grid::Array{Float64, 1}`: a grid of h2-values in [0, 1) where the optimization of profile likelihood    is performed; the finer the grid the better precision but longer wait-time. (default: 0.0:0.10:0.90, 10 values)

### Null-LMM through exact optimization (the Brent's method), multi-threaded: "null-exact"

  * `nb::Int64`: The number of sub-groups of the total number of traits; each group is processed independently and    the processes are parallelized (default: the number of threads of the current Julia session)
  * `nt_blas::Int64`: The number of threads BLAS library will be using (default: 1)

## Permutation Testing:

```
Currently permutation testing is only supported for single-trait scans.
```

## Structure of Weighted Residual Variances:

  * `weights::Array{Float64, 1}`: Optional weights for modeling unequal, weighted structure of the residual variances    of the trait (default: Missing, i.e. equal residual variances)

## Numerical Techniques - for stabilizing the heritability optimization step

  * `optim_interval::Int64`: The number of sub-divided regions of the interval [0, 1) of heritability to perform each    numerical optimization scheme (the Brent's method) on (default: 1, i.e. the entire interval)
  * `prior_variance::Float64`: Scale parameter of the prior Scaled Inv-Chisq distributed residual variances (default: 0)
  * `prior_sample_size::Float64`: Degree of freedom parameter of the prior Scaled Inv-Chisq distributed residual    variances (default: 0)
  * `decomp_scheme::String`: Keyword indicating the decomposition scheme for the kinship matrix; either by "eigen"    or "svd" decomposition (default: "eigen")

# Returned Values:

The output of the single-trait scan function is an object. Depending on the user inputs and options, the fields of     the output object will differ. For example, for the returned output named as `MT_out` as "multiple traits      outputs":

## Null-LMM ("null-grid", "null-exact"):

  * `MT_out.h2_null_list::Array{Float64, 1}`: a list of h2_null estimated for each trait
  * `MT_out.L::Array{Float64, 2}`: 2-dimensional array (dimension: p*m) consisting of the LOD scores for all input traits; each column    contains the LOD scores for one trait

## Exact-LMM ("alt-grid"):

  * `MT_out.h2_panel::Array{Float64, 2}`: 2-dimensional array (dimension: p*m) h2 estimated for each marker and    each trait; each column contains the h2 estimated for each marker for one trait
  * `MT_out.L::Array{Float64, 2}`: 2-dimensional array (dimension: p*m) consisting of the LOD scores for all input traits; each column    contains the LOD scores for one trait

## If the option for reporting p-values is on, the p-values results will be returned as:

  * `MT_out.log10Pvals_mat::Array{Float64, 2}`: 2-dimensional array (dimension: p*m) consisting of the -log10(p-values)

for each test (of association between each trait and each marker).
