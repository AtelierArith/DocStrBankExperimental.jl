```
fit_iht(y, x, z; k=10, d = Normal(), l=IdentityLink(),...)
```

Fits a model on design matrix (genotype data) `x`, response (phenotype) `y`,  and non-genetic covariates `z` on a specific sparsity parameter `k`. Only predictors in  `x` will be subject to sparsity constraint, unless `zkeep` keyword is specified. 

# Arguments:

  * `y`: Phenotype vector or matrix. Should be an `Array{T, 1}` (single traits) or   `Array{T, 2}` (multivariate Gaussian traits). For multivariate traits, each    column of `y` should be a sample.
  * `x`: Genotype matrix (an `Array{T, 2}` or `SnpLinAlg`). For univariate   analysis, samples are rows of `x`. For multivariate analysis, samples are   columns of `x` (i.e. input `Transpose(x)` for `SnpLinAlg`)
  * `z`: Matrix of non-genetic covariates of type `Array{T, 2}` or `Array{T, 1}`.   For univariate analysis, sample covariates are rows of `z`. For multivariate   analysis, sample covariates are columns of `z`. If this is not specified, an   intercept term will be included automatically. If `z` is specified, make sure   the first column (row) is all 1s to represent the intercept.

# Optional Arguments:

  * `k`: Number of non-zero predictors. Can be a constant or a vector (for group IHT).
  * `J`: The number of maximum groups (set as 1 if no group infomation available)
  * `d`: Distribution of phenotypes. Specify `Normal()` for quantitative traits,   `Bernoulli()` for binary traits, `Poisson()` or `NegativeBinomial()` for   count traits, and `MvNormal()` for multiple quantitative traits.
  * `l`: A link function. The recommended link functions are `l=IdentityLink()` for   quantitative traits, `l=LogitLink()` for binary traits, `l=LogLink()` for Poisson   distribution, and `l=Loglink()` for NegativeBinomial distribution. For multivariate   analysis, the choice of link does not matter.
  * `group`: vector storing (non-overlapping) group membership
  * `weight`: vector storing vector of weights containing prior knowledge on each SNP
  * `zkeep`: BitVector determining whether non-genetic covariates in `z` will be subject    to sparsity constraint. `zkeep[i] = true` means covariate `i` will NOT be projected.   Note covariates forced in the model are not subject to sparsity constraint `k`.
  * `est_r`: Symbol (`:MM`, `:Newton` or `:None`) to estimate nuisance parameters for negative binomial regression
  * `use_maf`: boolean indicating whether we want to scale projection with minor allele frequencies (see paper)
  * `debias`: boolean indicating whether we debias at each iteration
  * `verbose`: boolean indicating whether we want to print intermediate results
  * `tol`: used to track convergence
  * `max_iter`: is the maximum IHT iteration for a model to converge. Defaults to 200, or 100 for cross validation
  * `min_iter`: is the minimum IHT iteration before checking for convergence. Defaults to 5.
  * `max_step`: is the maximum number of backtracking per IHT iteration. Defaults 3
  * `io`: An `IO` object for displaying intermediate results. Default `stdout`.
  * `init_beta`: Whether to initialize beta values to univariate regression values.    Currently only Gaussian traits can be initialized. Default `false`.
  * `memory_efficient`: If `true,` it will cause ~1.1 times slow down but one only   needs to store the genotype matrix (requiring 2np bits for PLINK binary files   and `8np` bytes for other formats). If `memory_efficient=false`, one also need   to store a `8nk` byte matrix where `k` is the sparsity levels.

# Output

  * An `IHTResult` (for single-trait analysis) or `mIHTResult` (for multivariate analysis).

# Group IHT

If `k` is a constant, then each group will have the same sparsity level. To run doubly  sparse IHT with varying group sparsities, construct `k` to be a vector where `k[i]` indicates the max number of predictors for group `i`. 
