```
cv_iht(y, x, z; path=1:20, q=5, d=Normal(), l=IdentityLink(), ...)
```

For each model specified in `path`, performs `q`-fold cross validation and  returns the (averaged) deviance residuals. The purpose of this function is to find the best sparsity level `k`, obtained from selecting the model with the minimum out-of-sample error. Note sparsity is enforced on `x` only, unless `zkeep` keyword is specified. 

To check if multithreading is enabled, check output of `Threads.nthreads()`.

# Arguments:

  * `y`: Phenotype vector or matrix. Should be an `Array{T, 1}` (single traits) or   `Array{T, 2}` (multivariate Gaussian traits). For multivariate traits, each    column of `y` should be a sample.
  * `x`: Genotype matrix (an `Array{T, 2}` or `SnpLinAlg`). For univariate   analysis, samples are rows of `x`. For multivariate analysis, samples are   columns of `x` (i.e. input `Transpose(x)` for `SnpLinAlg`)
  * `z`: Matrix of non-genetic covariates of type `Array{T, 2}` or `Array{T, 1}`.   For univariate analysis, sample covariates are rows of `z`. For multivariate   analysis, sample covariates are columns of `z`. If this is not specified, an   intercept term will be included automatically. If `z` is specified, make sure   the first column (row) is all 1s to represent the intercept.

# Optional Arguments:

  * `path`: Different values of `k` that should be tested. One can input a vector of    `Int` (e.g. `path=[5, 10, 15, 20]`) or a range (default `path=1:20`).
  * `q`: Number of cross validation folds. Larger means more accurate and more computationally   intensive. Should be larger 2 and smaller than 10. Default `q=5`.
  * `d`: Distribution of phenotypes. Specify `Normal()` for quantitative traits,   `Bernoulli()` for binary traits, `Poisson()` or `NegativeBinomial()` for   count traits, and `MvNormal()` for multiple quantitative traits.
  * `l`: A link function. The recommended link functions are `l=IdentityLink()` for   quantitative traits, `l=LogitLink()` for binary traits, `l=LogLink()` for Poisson   distribution, and `l=Loglink()` for NegativeBinomial distribution. For multivariate   analysis, the choice of link does not matter.
  * `zkeep`: BitVector determining whether non-genetic covariates in `z` will be subject    to sparsity constraint. `zkeep[i] = true` means covariate `i` will NOT be projected.   Note covariates forced in the model are not subject to sparsity constraints in `path`.
  * `est_r`: Symbol (`:MM`, `:Newton` or `:None`) to estimate nuisance parameters for negative binomial regression
  * `group`: vector storing group membership for each predictor
  * `weight`: vector storing vector of weights containing prior knowledge on each predictor
  * `folds`: Vector that separates the sample into `q` disjoint subsets
  * `debias`: Boolean indicating whether we should debias at each IHT step. Defaults `false`
  * `verbose`: Boolean indicating whether to print progress and mean squared error for   each `k` in `path`. Defaults `true`
  * `max_iter`: is the maximum IHT iteration for a model to converge. Defaults to 100
  * `min_iter`: is the minimum IHT iteration before checking for convergence. Defaults to 5.
  * `init_beta`: Whether to initialize beta values to univariate regression values.    Currently only Gaussian traits can be initialized. Default `false`.
  * `memory_efficient`: If `true,` it will cause ~1.1 times slow down but one only   needs to store the genotype matrix (requiring 2np bits for PLINK binary files   and `8np` bytes for other formats). If `memory_efficient=false`, one may potentially   store `t` sparse matrices of dimension `8nk` bytes where `k` are the cross validated   sparsity levels.

# Output

  * `mse`: A vector of mean-squared error for each `k` specified in `path`.
