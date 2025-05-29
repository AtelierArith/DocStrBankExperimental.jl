```
sec_filings(fmp, symbol, params...)
```

Returns sec filings for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol or "all" if not provided.
  * `params...`: Additional keyword query params.

See [SEC-Filings](https://site.financialmodelingprep.com/developer/docs/#SEC-Filings) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the first page of 10-K filings for AAPL
data = sec_filings(fmp, "AAPL", type = "10-K", page = 0)
```
