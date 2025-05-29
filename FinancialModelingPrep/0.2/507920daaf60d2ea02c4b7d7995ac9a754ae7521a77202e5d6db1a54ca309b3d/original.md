```
company_rating(fmp, symbol)
```

Returns ratings for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.

See [Company-Rating](https://site.financialmodelingprep.com/developer/docs/#Company-Rating) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the company rating for AAPL 
data = company_rating(fmp, "AAPL")
```
