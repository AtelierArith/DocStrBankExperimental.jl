```
har_est(x::Array; m::Array = [1 , 5 , 22])
```

Estimates the parameters of the Heterogenous Autoregressive (HAR) model given the data `x`. See [Corsi (2009)](https://academic.oup.com/jfec/article/7/2/174/856522).

# Arguments

  * `x::Array`: The data.

# Optional arguments

  * `m::Array`: An array with the lags to use in the estimation. By default, the lags are 1, 5, and 22; as suggested by the original paper.

# Output

  * `β::Array`: The estimated parameters of the HAR model.
  * `σ::Real`: The estimated standard deviation of the HAR model.

# Examples

```julia
julia> har_est(randn(100,1))
```
