```
institution_portfolio_dates(fmp, cik)
```

Returns the portfolio dates for the specified institution.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `cik::String`: A CIK.

See [Institutional-Holders-Available-Date](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holders-Available-Date) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the portfolio dates for Berkshire Hathaway
data = institution_portfolio_dates(fmp, cik = "0001067983")
```
