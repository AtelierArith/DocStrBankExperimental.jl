```
financial_reports(fmp, symbol, year, period = "FY")
```

Returns a JSON dictionary of the financial report for the specified symbol, year and period.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `year::Integer`: A calendar year.
  * `period::String`: One of "FY", "Q1", "Q2", "Q3" or "Q4".

See [Annual-Reports-on-Form-10-K](https://site.financialmodelingprep.com/developer/docs#Annual-Reports-on-Form-10-K) for more details.
See [Quarterly-Earnings-Reports](https://site.financialmodelingprep.com/developer/docs/#Quarterly-Earnings-Reports) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the 10-K for AAPL in 2022
data = financial_reports(fmp, "AAPL", year = 2022)

# get the 10-Q for AAPL in Q4 of 2022
data = financial_reports(fmp, "AAPL", 2022, period = "Q4")
```
