```
predict(m,X; Xpos=Xpos, <keyword arguments>)
```

Predict using a fitted TwoPartModel given new X (and potentially Xpos).

# Example with GLM:

```julia
  m = fit(Hurdle,GeneralizedLinearModel,X,y; Xpos=Xpos)
  yhat = predict(m, X; Xpos=Xpos)
```

# Example with Lasso regularization:

```julia
  m = fit(Hurdle,GammaLassoPath,X,y; Xpos=Xpos)
  yhat = predict(m, X; Xpos=Xpos, select=MinAICc())
```

# Arguments

  * `m::Hurdle` fitted Hurdle model
  * `X` n-by-p matrix of covariates of same dimensions used to fit m.

# Keywords

  * `Xpos::Union{AbstractMatrix{T},Nothing} = nothing` covariates matrix for positives model or nothing to use X for both parts
  * `kwargs...` additional keyword arguments passed along to predict() for each of the two model parts.
