```
institution_portfolio_composition(fmp, cik, params...)
```

Returns the portfolio composition for the specified institution.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `cik::String`: A CIK.
  * `params...`: Additional keyword query params.

See [Institutional-Holdings-Portfolio-Composition](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holdings-Portfolio-composition) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the portfolio composition for Berkshire Hathaway in Q3 of 2021
data = institution_portfolio_composition(fmp, cik = "0001067983", date = "2021-09-30")
```
