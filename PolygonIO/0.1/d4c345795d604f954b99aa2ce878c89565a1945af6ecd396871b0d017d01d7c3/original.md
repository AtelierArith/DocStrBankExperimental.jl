```
ticker_details_vX(opts::PolyOpts, ticker::AbstractString, date::AbstractString)
```

Get a single ticker supported by Polygon.io. This response will have detailed information about the ticker and the company behind it.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.
  * ticker::AbstractString - The ticker symbol of the asset.
  * date::AbstractString - Specify a point in time to get information about the ticker available on that date. When retrieving information from SEC filings, we compare this date with the period of report date on the SEC filing.

For example, consider an SEC filing submitted by AAPL on 2019-07-31, with a period of report date ending on 2019-06-29. That means that the filing was submitted on 2019-07-31, but the filing was created based on information from 2019-06-29. If you were to query for AAPL details on 2019-06-29, the ticker details would include information from the SEC filing. Defaults to the most recent available date.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> ticker_details_vX(opts, "AAPL", "2017-01-01")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*vX*reference_tickers**ticker**anchor for documentation on response attributes and supported keyword arguments.
