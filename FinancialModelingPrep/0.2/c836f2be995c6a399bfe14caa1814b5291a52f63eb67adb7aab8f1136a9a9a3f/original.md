```
symbols_with_financials(fmp)
```

Returns a JSON array of symbols which have financial statements.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Financial-Statements-List](https://site.financialmodelingprep.com/developer/docs#Financial-Statements-List) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get a list of all symbols with financials
data = symbols_with_financials(fmp)
```
