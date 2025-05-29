tickers(opts::PolyOpts, search::AbstractString;         active=true, sort="ticker", order="asc", limit=10, kwargs...)

Query all ticker symbols which are supported by Polygon.io. This API currently includes Stocks/Equities, Crypto, and Forex.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.
  * search::AbstractString - Search for terms within the ticker and/or company name.
  * active::Boolean - Specify if the tickers returned should be actively traded on the queried date. Default is true.
  * sort::String - The field to sort the results on. Default is ticker. If the search query parameter is present, sort is ignored and results are ordered by relevance.
  * order::String - The order to sort the results on. Default is asc (ascending).
  * limit::Integer - Limit the size of the response, default is 100 and max is 1000. If your query returns more than the max limit and you want to retrieve the next page of results, see the next_url response attribute.
  * kwargs::Dict - Additional query parameters.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> tickers(opts, "bitcoin")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v3*reference*tickers*anchor for documentation on response attributes and supported keyword arguments.
