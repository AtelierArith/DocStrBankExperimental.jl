```
market_risk_premiums(fmp)
```

Returns market risk premiums for each country.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Market-Risk-Premium](https://site.financialmodelingprep.com/developer/docs/#Market-Risk-Premium) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all market risk premiums
data = market_risk_premiums(fmp)
```
