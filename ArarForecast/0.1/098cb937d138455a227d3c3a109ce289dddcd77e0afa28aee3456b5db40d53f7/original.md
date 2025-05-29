arar(y::TimeArray, h::Int, freq::DataType, max_lag::Int)

Forecasting using ARAR algorithm.

Return A matrix of forecast values and prediction intervals

# Arguments

  * `y::TimeArray`: An TimeArray with only one value column.
  * `h::Int`: Forecast horizon as an integer.
  * `freq::DataType`: A DataType from Dates, e.g. Dates.Day or Dates.Month.
  * `max_lag::Int`: An integer (>= 26) to specify maximum number of lags for sample autocovariance.

# Examples

```julia-repl
julia> arar(data, 12, Month)

```
