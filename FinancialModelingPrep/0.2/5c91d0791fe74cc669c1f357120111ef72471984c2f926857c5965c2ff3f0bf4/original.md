```
etf_portfolio_dates(fmp, symbol)
etf_portfolio_dates(fmp, cik)
```

Returns the portfolio dates for the specified ETF.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `cik::String`: A CIK.

See [Historical-Mutual-Fund-Holdings-Available-Dates](https://site.financialmodelingprep.com/developer/docs/#historical-mutual-fund-holdings-available-dates) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the portfolio dates for VOO
data = etf_portfolio_dates(fmp, "VOO")

# get the portfolio dates for DLR
data = etf_portfolio_dates(fmp, cik = "0000036405")
```
