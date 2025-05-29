```
senate_disclosures(fmp, symbol)
```

Returns senate disclosures for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Senate-Disclosure](https://site.financialmodelingprep.com/developer/docs/#Senate-disclosure) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get senate disclosures for AAPL
data = senate_disclosures(fmp, "AAPL")
```
