```
search_symbol(fmp, symbol, params...)
```

Returns search results for the specified symbol and filters.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Symbol-Search](https://site.financialmodelingprep.com/developer/docs/#Ticker-Search) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first 10 matches where symbol is AA and exchange is NASDAQ
data = search_symbol(fmp, "AA", limit = 10, exchange = "NASDAQ")
```
