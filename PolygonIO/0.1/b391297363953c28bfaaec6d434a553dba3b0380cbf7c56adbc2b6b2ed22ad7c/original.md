```
ticker_news(opts::PolyOpts, ticker::AbstractString;
            published_utc_gte="2021-04-26", limit=10,
            order="descending", sort="published_utc",kwargs...)
```

Get the most recent news articles relating to a stock ticker symbol, including a summary of the article and a link to the original source.

# Arguments

  * opts::PolyOpts - The PolyOpts object used to configure the request.
  * ticker::AbstractString - Ticker symbol. Return results where this field equals the value.
  * published*utc*gte::AbstractString - Return results where this field is greater than or equal to the value.
  * limit::Integer - Limit the size of the response, default is 100 and max is 1000.  If your query returns more than the max limit and you want to retrieve the next page of results, see the next_url response attribute.
  * order::String - Order the results in ascending or descending order.
  * sort::String - The field key to sort the results on.
  * kwargs::Dict - Additional query parameters

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> ticker_news(opts, "AAPL", limit=5)
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array.
  * See https://polygon.io/docs/get*v2*reference*news*anchor for documentation on response attributes and supported keyword arguments.
