```
forex_aggregates_bars(opts::PolyOpts, forexTicker="C:EURUSD", multiplier=1, timespan="day", from="2020-10-14", to="2020-10-14";
                    adjusted=true, sort="asc", limit=120)
```

Get aggregate bars for a forex pair over a given date range in custom time window sizes. For example, if timespan = ‘minute’ and multiplier = ‘5’ then 5-minute bars will be returned.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * forexTicker: The ticker symbol of the currency pair.
  * multiplier: The size of the timespan multiplier.
  * timespan: The size of the time window.
  * from: The start of the aggregate time window.
  * to: The end of the aggregate time window.
  * adjusted: Whether or not the results are adjusted for splits.  By default, results are adjusted. Set this to false to get results that are NOT adjusted for splits.
  * sort: Sort the results by timestamp. asc will return results in ascending order (oldest at the top),  desc will return results in descending order (newest at the top).
  * limit: Limits the number of base aggregates queried to create the aggregate results. Max 50000 and Default 120.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> forex_aggregates_bars(opts, "C:EURUSD", "5", "minute", "2020-10-14", "2020-10-14")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*aggs_ticker**forexTicker**range**multiplier___timespan___from___to**anchor for documentation on response attributes and supported keyword arguments.
