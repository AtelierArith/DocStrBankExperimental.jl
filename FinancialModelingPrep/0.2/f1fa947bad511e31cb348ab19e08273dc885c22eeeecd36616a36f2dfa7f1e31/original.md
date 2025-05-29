```
institution_portfolio_summary(fmp, cik)
```

Returns the portfolio summary for the specified institution.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `cik::String`: A CIK.

See [Institutional-Holdings-Portfolio-Positions-Summary](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holdings-Portfolio-Positions-Summary) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the portfolio summary for Berkshire Hathaway
data = institution_portfolio_summary(fmp, cik = "0001067983")
```
