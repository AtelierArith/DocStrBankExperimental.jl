```
stocks_quotes_nbbo(opts::PolyOpts, ticker::AbstractString, date::AbstractString; limit=10, reverse=true, kwargs...)
```

Get NBBO quotes for a given ticker symbol on a specified date.

# Arguments

  * opts::PolyOpts: The PolyOpts object used to configure the request.
  * ticker::AbstractString: The ticker symbol we want quotes for.
  * date::AbstractString: The date/day of the quotes to retrieve in the format YYYY-MM-DD.
  * limit::Int: Limit the size of the response, max 50000 and default 10.
  * reverse::Bool: Reverse the order of the results.
  * kwargs::Any: A list of additional arguments to pass to the Polygon IO API.

# Example

```julia-repl
julia> opts = PolyOpts(API_KEY, nothing)
julia> stocks_quotes_nbbo(opts, "AAPL", "2017-01-01")
```

# Returns

  * A JSON3.Array or specified tabular representation of the JSON3.Array
  * See https://polygon.io/docs/get*v2*ticks*stocks*nbbo**ticker___date**anchor for documentation on response attributes and supported keyword arguments.
