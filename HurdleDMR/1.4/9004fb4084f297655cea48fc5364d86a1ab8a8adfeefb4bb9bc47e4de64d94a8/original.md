```
fit(InclusionRepetition,M,X,y; Xpos=Xpos, <keyword arguments>)
```

Fit an Inclusion-Repetition model of count vector y on X with potentially another covariates matrix Xpos used to model positive counts (repetitions).

# Example with GLM:

```julia
  m = fit(InclusionRepetition,GeneralizedLinearModel,X,y; Xpos=Xpos)
  yhat = predict(m, X; Xpos=Xpos)
```

# Example with Lasso regularization:

```julia
  m = fit(InclusionRepetition,GammaLassoPath,X,y; Xpos=Xpos)
  yhat = predict(m, X; Xpos=Xpos, select=MinAICc())
```

# Arguments

  * `M::RegressionModel`
  * `counts` n-by-d matrix of counts (usually sparse)
  * `dzero::UnivariateDistribution = Binomial()` distribution for zeros (inclusion) model
  * `dpos::UnivariateDistribution = Poisson()` distribution for positives (repetition) model
  * `lzero::Link=canonicallink(dzero)` link function for zeros model
  * `lpos::Link=canonicallink(dpos)` link function for positives model

# Keywords

  * `Xpos::Union{AbstractMatrix{T},Nothing} = nothing` covariates matrix for positives model or nothing to use X for both parts
  * `dofit::Bool = true` fit the model or just construct its shell
  * `wts::V = ones(y)` observation weights
  * `offsetzero::AbstractVector = similar(y, 0)` offsets for zeros model
  * `offsetpos::AbstractVector = similar(y, 0)` offsets for positives model
  * `offset::AbstractVector = similar(y, 0)` offsets for both model parts
  * `verbose::Bool=true`
  * `showwarnings::Bool=false`
  * `fitargs...` additional keyword arguments passed along to fit(M,...)
