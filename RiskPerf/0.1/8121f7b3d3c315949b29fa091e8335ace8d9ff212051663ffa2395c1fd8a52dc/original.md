```
log_returns(prices::Matrix; drop_first=false, first_value=NaN)
```

Calculates log-return series for each column of the provided prices matrix, where each column denotes a prices series of an asset, e.g. a stock.

Please note that the provided prices series should be regularly spaced, for example hourly or daily data.

# Arguments

  * `prices`: Matrix of size `[N x k]` of prices, where each column denotes a price series of an asset, e.g. a stock.
  * `drop_first`: Boolean value indicating whether to drop the first return or not (default=false).
  * `first_value`: Value to be used for the first return if `drop_first=false`.

# Formula

$r_{t, i} = \log\left(\dfrac{P_{t, i}}{P_{t-1, i}}\right)$

where $r_{t, i}$ is the return at time $t$ for asset $i$, $P_{t, i}$ is the price at time $t$ for asset $i$, and $P_{t-1, i}$ is the price at time $t-1$ for asset $i$.

# Examples

```jldoctest
julia> using RiskPerf

julia> prices = [100.0 99.0; 101.0 99.5; 100.5 99.8; 99.8 99.2; 101.3 100.0]
5×2 Matrix{Float64}:
 100.0   99.0
 101.0   99.5
 100.5   99.8
  99.8   99.2
 101.3  100.0

julia> log_returns(prices)
5×2 Matrix{Float64}:
 NaN           NaN
   0.00995033    0.00503779
  -0.00496279    0.00301054
  -0.00698954   -0.00603017
   0.0149182     0.00803217

julia> log_returns(prices; drop_first=true)
4×2 Matrix{Float64}:
  0.00995033   0.00503779
 -0.00496279   0.00301054
 -0.00698954  -0.00603017
  0.0149182    0.00803217
```
