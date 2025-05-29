```
fit(LassoPath, X, y, d=Normal(), l=canonicallink(d); ...)
```

fits a linear or generalized linear Lasso path given the design matrix `X` and response `y`:

$\underset{\beta,b_0}{\operatorname{argmin}} -\frac{1}{N} \mathcal{L}(y|X,\beta,b_0) + \lambda\left[(1-\alpha)\frac{1}{2}\|\beta\|_2^2 + \alpha\|\beta\|_1\right]$

where $0 \le \alpha \le 1$ sets the balance between ridge ($\alpha = 0$) and lasso ($\alpha = 1$) regression, and $N$ is the number of rows of $X$. The optional argument `d` specifies the conditional distribution of response, while `l` specifies the link function. Lasso.jl inherits supported distributions and link functions from GLM.jl. The default is to fit an linear Lasso path, i.e., `d=Normal(), l=IdentityLink()`, or $\mathcal{L}(y|X,\beta) = -\frac{1}{2}\|y - X\beta - b_0\|_2^2 + C$

# Examples

```julia
fit(LassoPath, X, y)    # L1-regularized linear regression
fit(LassoPath, X, y, Binomial(), Logit();
    α=0.5) # Binomial logit regression with an Elastic net combination of
           # 0.5 L1 and 0.5 L2 regularization penalties
```

# Arguments

  * `wts=ones(length(y))`: Weights for each observation
  * `offset=zeros(length(y))`: Offset of each observation
  * `λ`: can be used to specify a specific set of λ values at which models are fit.   You can pass an `AbstractVector` of explicit values for `λ`, or a function   `λfunc(λmax)` returning such values, where `λmax` will be the smallest `λ`   value yielding a null model.   If `λ` is unspecified, Lasso.jl selects `nλ` logarithmically spaced `λ` values from   `λmax` to `λminratio * λmax`.
  * `α=1`: Value between 0 and 1 controlling the balance between ridge ($\alpha = 0$)   and lasso ($\alpha = 1$) regression.   `α` cannot be set to 0 if `λ` was not specified , though it may be set to 1.
  * `nλ=100` number of `λ` values to use
  * `λminratio=1e-4` if more observations than predictors otherwise 0.001.
  * `stopearly=true`: When `true`, if the proportion of deviance explained   exceeds 0.999 or the difference between the deviance explained by successive λ   values falls below `1e-5`, the path stops early.
  * `standardize=true`: Whether to standardize predictors to unit standard deviation   before fitting.
  * `intercept=true`: Whether to fit an (unpenalized) model intercept $b_0$. If false, $b_0=0$.
  * `algorithm`: Algorithm to use.   `NaiveCoordinateDescent` iteratively computes the dot product of the   predictors with the  residuals, as opposed to the   `CovarianceCoordinateDescent` algorithm, which uses a precomputed Gram matrix.   `NaiveCoordinateDescent` is typically faster when there are many   predictors that will not enter the model or when fitting   generalized linear models.   By default uses `NaiveCoordinateDescent` if more than 5x as many predictors   as observations or model is a GLM. `CovarianceCoordinateDescent` otherwise.
  * `randomize=true`: Whether to randomize the order in which coefficients are   updated by coordinate descent. This can drastically speed   convergence if coefficients are highly correlated.
  * `rng=RNG_DEFAULT`: Random number generator to be used for coefficient iteration.
  * `maxncoef=min(size(X, 2), 2*size(X, 1))`: maximum number of coefficients   allowed in the model. If exceeded, an error will be thrown.
  * `dofit=true`: Whether to fit the model upon construction. If `false`, the   model can be fit later by calling `fit!(model)`.
  * `cd_maxiter=100_000`: The maximum number of coordinate descent iterations.
  * `cd_tol=1e-7`: The tolerance for coordinate descent iterations iterations in   the inner loop.
  * `irls_maxiter=30`: Maximum number of iterations in the iteratively reweighted  least squares loop. This is ignored unless the model is a generalized linear  model.
  * `irls_tol=1e-7`: The tolerance for outer iteratively reweighted least squares   iterations. This is ignored unless the model is a generalized linear model.
  * `criterion=:coef` Convergence criterion. Controls how `cd_tol` and `irls_tol`   are to be interpreted. Possible values are:

      * `:coef`: The model is considered to have converged if the the maximum absolute squared difference in coefficients between successive iterations drops below the specified tolerance. This is the criterion used by glmnet.
      * `:obj`: The model is considered to have converged if the the relative change in the Lasso/Elastic Net objective between successive iterations drops below the specified tolerance. This is the criterion used by GLM.jl.
  * `minStepFac=0.001`: The minimum step fraction for backtracking line search.
  * `penalty_factor=ones(size(X, 2))`: Separate penalty factor $\omega_j$   for each coefficient $j$, i.e. instead of $\lambda$ penalties become   $\lambda\omega_j$.   Note the penalty factors are internally rescaled to sum to   the number of variables (`glmnet.R` convention).
  * `standardizeω=true`: Whether to scale penalty factors to sum to the number of   variables (glmnet.R convention).
