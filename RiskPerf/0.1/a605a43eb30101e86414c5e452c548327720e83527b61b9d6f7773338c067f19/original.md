```
simple_returns(prices::Matrix; drop_first=false, first_value=NaN)
```

Calculates the simple returns series for each column of the provided prices matrix, where each column denotes a prices series of an asset, e.g. a stock.

Please note that the provided prices series should be regularly spaced, for example hourly or daily data.

# Arguments

  * `prices`: Matrix of size `[N x k]` where each column denotes a price series of an asset, e.g. a stock.
  * `drop_first`: Boolean value indicating whether to drop the first return or not (default=false).
  * `first_value`: Value to be used for the first return if `drop_first=false`.

# Formula

$r_{t, i} = \dfrac{P_{t, i}}{P_{t-1, i}} - 1$

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

julia> simple_returns(prices)
5×2 Matrix{Float64}:
 NaN           NaN
   0.01          0.00505051
  -0.0049505     0.00301508
  -0.00696517   -0.00601202
   0.0150301     0.00806452

julia> simple_returns(prices; drop_first=true)
4×2 Matrix{Float64}:
  0.01         0.00505051
 -0.0049505    0.00301508
 -0.00696517  -0.00601202
  0.0150301    0.00806452
```
