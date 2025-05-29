```
infcrit(r)
```

Calculate adjusted R², Akaike’s Information Criterion (AIC) and Bayesian Information Criterion (BIC) for a linear regression model `r`.

# Arguments

  * `r::FixedEffectModel`: linear regression model

# Returns

Named tuple containing:

  * `r2adj::Float64`: adjusted R²
  * `aic::Float64`: Akaike’s Information Criterion
  * `bic::Float64`: Bayesian Information Criterion
