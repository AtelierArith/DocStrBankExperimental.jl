```
hamilton_filter(y::AbstractVector, h::Integer, p::Integer; subset)
hamilton_filter(y::AbstractVector, freq::Symbol; subset)
```

Decompose the time series in `y` into a cyclical component and a trend component using the method by Hamilton (2018).

Rows in `y` that involve invalid values (e.g., `NaN`, `Inf` and `missing`) for estimation are skipped. Returned vectors are of the same length as `y`.

# Arguments

  * `y::AbstractVector`: vector storing the time series to be filtered.
  * `h::Integer`: horizon of forcasting; for business cycles, should cover 2 years.
  * `p::Integer`: number of lags used for estimation, including the contemporary one.
  * `freq::Symbol`: use default values of `h` and `p` suggested by Hamilton (2018) based on data frequency; must be `:m`, `:q` or `:y` for monthly, quarterly or annual data.

# Keywords

  * `subset::Union{BitVector,Nothing}=nothing`: Boolean indices of rows in `y` to be filtered.

# Returns

  * `Vector{Float64}`: the cyclical component.
  * `Vector{Float64}`: the trend component.
  * `BitVector`: indicators for whether an estimate is obtained for each row of input data `y`.

# Reference

Hamilton, James D. 2018. "Why You Should Never Use the Hodrick-Prescott Filter." The Review of Economics and Statistics 100 (5): 831-843.
