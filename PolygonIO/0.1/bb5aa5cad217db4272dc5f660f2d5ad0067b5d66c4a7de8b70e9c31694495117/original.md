```
stocks_aggregates_bars(opts::PolyOpts, stocksTicker::AbstractString;
                    multiplier=1, timespan="day", from="2020-10-14", to="2020-10-14",
                    adjusted=true, sort="asc", limit=120, kwargs...)
```

Get aggregate bars for a stock over a given date range in custom time window sizes. For example, if timespan = ‘minute’ and multiplier = ‘5’ then 5-minute bars will be returned.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * stocksTicker::AbstractString: The ticker symbol of the stock/equity.
  * multiplier::Int: TThe size of the timespan multiplier.
  * timespan::AbstractString: The size of the time window.
  * from::AbstractString: The start of the aggregate time window.
  * to::AbstractString: The end of the aggregate time window.
  * adjusted::Bool: Whether or not the results are adjusted for splits.  By default, results are adjusted. Set this to false to get results that are NOT adjusted for splits.
  * sort::AbstractString: Sort the results by timestamp. asc will return results in ascending order (oldest at the top),  desc will return results in descending order (newest at the top).
  * limit::Int: Limits the number of base aggregates queried to create the aggregate results. Max 50000 and Default 120.
  * kwargs::AbstractString: Any additional arguments.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_aggregates_bars(opts, "AAPL", multiplier=5, timespan="minute", from="2017-01-01", to="2017-01-01")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*aggs_ticker**stocksTicker**range**multiplier___timespan___from___to**anchor for documentation on response attributes and supported keyword arguments.
