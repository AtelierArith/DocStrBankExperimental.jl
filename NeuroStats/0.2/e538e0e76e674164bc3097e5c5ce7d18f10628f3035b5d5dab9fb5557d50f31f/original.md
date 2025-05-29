```
infcrit(m)
```

Calculate R², R² adjusted, Akaike’s Information Criterion (AIC) and Bayesian Information Criterion (BIC) for a linear regression model `m`.

# Arguments

  * `m::StatsModels.TableRegressionModel`: linear regression model

# Returns

Named tuple containing:

  * `R2::Float64`
  * `R2adj::Float64`
  * `bic::Float64`
  * `bic::Float64`
