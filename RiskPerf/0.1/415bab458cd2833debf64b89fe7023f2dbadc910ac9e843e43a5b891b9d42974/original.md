```
log_returns(prices::Vector; drop_first=false, first_value=NaN)
```

Calculates the log-return series based on the provided time series of `N` prices. Please note that the provided prices series should be regularly spaced, for example hourly or daily data.

# Arguments

  * `prices`: Vector of prices.
  * `drop_first`: Boolean value indicating whether to drop the first return or not (default=false).
  * `first_value`: Value to be used for the first return if `drop_first=false`.

# Formula

$r_t = \log\left(\dfrac{P_t}{P_{t-1}}\right)$

where $r_t$ is the return at time $t$, $P_t$ is the price at time $t$, and $P_{t-1}$ is the price at time $t-1$.

# Examples

```jldoctest
julia> using RiskPerf

julia> prices = [100.0, 101.0, 100.5, 99.8, 101.3]
5-element Vector{Float64}:
 100.0
 101.0
 100.5
  99.8
 101.3

julia> log_returns(prices)
5-element Vector{Float64}:
 NaN
   0.009950330853168092
  -0.004962789342129014
  -0.006989544181712186
   0.014918227937219366

julia> log_returns(prices; drop_first=true)
4-element Vector{Float64}:
  0.009950330853168092
 -0.004962789342129014
 -0.006989544181712186
  0.014918227937219366
```
