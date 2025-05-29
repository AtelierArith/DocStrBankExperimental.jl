```
fit(RegularizedModel, X, y, dist, link; <kwargs>)
```

Returns a LinearModel or GeneralizedLinearModel representing the selected segment of a regularization path.

# Examples

```julia
fit(LassoModel, X, y; select=MinBIC()) # BIC minimizing LinearModel
fit(LassoModel, X, y, Binomial(), Logit();
    select=MinCVmse(path, 5)) # 5-fold CV mse minimizing model
```

# Arguments

  * `select::SegSelect=MinAICc()`: segment selector.
  * `wts=ones(length(y))`: Weights for each observation
  * `offset=zeros(length(y))`: Offset of each observation
  * `λ`: can be used to specify a specific set of λ values at which models are fit.   If λ is unspecified, Lasso.jl selects nλ logarithmically spaced λ values from   `λmax`, the smallest λ value yielding a null model, to   `λminratio * λmax`.
  * `nλ=100` number of λ values to use
  * `λminratio=1e-4` if more observations than predictors otherwise 0.001.
  * `stopearly=true`: When `true`, if the proportion of deviance explained   exceeds 0.999 or the difference between the deviance explained by successive λ   values falls below `1e-5`, the path stops early.
  * `standardize=true`: Whether to standardize predictors to unit standard deviation   before fitting.
  * `intercept=true`: Whether to fit an (unpenalized) model intercept.
  * `algorithm`: Algorithm to use.   `NaiveCoordinateDescent` iteratively computes the dot product of the   predictors with the  residuals, as opposed to the   `CovarianceCoordinateDescent` algorithm, which uses a precomputed Gram matrix.   `NaiveCoordinateDescent` is typically faster when there are many   predictors that will not enter the model or when fitting   generalized linear models.   By default uses `NaiveCoordinateDescent` if more than 5x as many predictors   as observations or model is a GLM. `CovarianceCoordinateDescent` otherwise.
  * `randomize=true`: Whether to randomize the order in which coefficients are   updated by coordinate descent. This can drastically speed   convergence if coefficients are highly correlated.
  * `maxncoef=min(size(X, 2), 2*size(X, 1))`: maximum number of coefficients   allowed in the model. If exceeded, an error will be thrown.
  * `dofit=true`: Whether to fit the model upon construction. If `false`, the   model can be fit later by calling `fit!(model)`.
  * `cd_tol=1e-7`: The tolerance for coordinate descent iterations iterations in   the inner loop.
  * `irls_tol=1e-7`: The tolerance for outer iteratively reweighted least squares   iterations. This is ignored unless the model is a generalized linear model.
  * `criterion=:coef` Convergence criterion. Controls how `cd_tol` and `irls_tol`   are to be interpreted. Possible values are:

      * `:coef`: The model is considered to have converged if the the maximum absolute squared difference in coefficients between successive iterations drops below the specified tolerance. This is the criterion used by glmnet.
      * `:obj`: The model is considered to have converged if the the relative change in the Lasso/Elastic Net objective between successive iterations drops below the specified tolerance. This is the criterion used by GLM.jl.
  * `minStepFac=0.001`: The minimum step fraction for backtracking line search.
  * `penalty_factor=ones(size(X, 2))`: Separate penalty factor $\omega_j$   for each coefficient $j$, i.e. instead of $\lambda$ penalties become   $\lambda\omega_j$.   Note the penalty factors are internally rescaled to sum to   the number of variables (`glmnet.R` convention).
  * `standardizeω=true`: Whether to scale penalty factors to sum to the number of   variables (glmnet.R convention).

See also [`fit(::Type{LassoPath}, ::Matrix{Float64}, ::Vector{Float64})`](@ref) for a more complete list of arguments
