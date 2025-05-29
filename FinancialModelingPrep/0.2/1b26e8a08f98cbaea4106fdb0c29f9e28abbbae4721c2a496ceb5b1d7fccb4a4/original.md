```
company_information(fmp, symbol)
```

Returns company information for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Stock-Peers](https://site.financialmodelingprep.com/developer/docs/#Stock-Peers) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the company information for AAPL
data = company_information(fmp, "AAPL")
```
