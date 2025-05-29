```
etf_portfolio(fmp, symbol, params...)
etf_portfolio(fmp, cik, params...)
```

Returns the portfolio for the specified ETF.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `cik::String`: A CIK.
  * `params...`: Additional keyword query params.

See [Historical-Mutual-Fund-Holdings-Portfolio](https://site.financialmodelingprep.com/developer/docs/#historical-mutual-fund-holdings-portfolio) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the portfolio for VOO at the end of 2021
data = etf_portfolio(fmp, "VOO", date = "2021-12-31")

# get the portfolio for DLR at the end of 2021
data = etf_portfolio(fmp, cik = "0000036405", date = "2021-12-31")
```
