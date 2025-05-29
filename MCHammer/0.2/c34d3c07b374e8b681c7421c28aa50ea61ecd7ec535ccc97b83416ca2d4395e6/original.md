```
forecast_uncertainty(HistoricalData::Vector{<:Real}, PeriodsToForecast::Int) -> Vector{Float64}
```

Calculate forecast uncertainty multipliers based on historical data volatility.

This function computes the percentage returns from the historical data, estimates the standard deviation (σ) of those returns, and then generates a vector of forecast multipliers. Each multiplier is calculated as:

$u = 1 + \sigma \cdot \epsilon$

where ($\epsilon$) is a random sample drawn from a standard normal distribution          $\epsilon \sim \mathcal{N}(0,1)$ and $\sigma$ is the standard deviation of the historical percentage returns.

# Arguments

  * `HistoricalData::Vector{<:Real}`: A vector of historical observations (e.g., prices, values).
  * `PeriodsToForecast::Int`: The number of forecast periods for which to generate uncertainty multipliers.

# Returns

  * A vector of length `PeriodsToForecast` containing the forecast uncertainty multipliers. These multipliers can be used to perturb a base forecast to simulate forecast variability.
