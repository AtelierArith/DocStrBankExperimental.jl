```
mutual_fund_portfolio_dates(fmp, symbol)
mutual_fund_portfolio_dates(fmp, cik)
```

Returns the portfolio dates for the specified mutual fund.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `cik::String`: A CIK.

See [Historical-Mutual-Fund-Holdings-Available-Dates](https://site.financialmodelingprep.com/developer/docs/#historical-mutual-fund-holdings-available-dates) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the portfolio dates for VTSAX
data = mutual_fund_portfolio_dates(fmp, "VTSAX")

# get the portfolio dates for VEXPX
data = mutual_fund_portfolio_dates(fmp, cik = "0000034066")
```
