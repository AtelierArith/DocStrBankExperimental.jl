```
institution_portfolio_industry_summary(fmp, cik, params...)
```

Returns the portfolio industry summary for the specified institution.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `cik::String`: A CIK.
  * `params...`: Additional keyword query params.

See [Institutional-Holdings-Portfolio-Industry-Summary](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holdings-Portfolio-Industry-Summary) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the portfolio industry summary for Berkshire Hathaway in Q3 of 2021
data = institution_portfolio_industry_summary(fmp, cik = "0001067983", date = "2021-09-30")
```
