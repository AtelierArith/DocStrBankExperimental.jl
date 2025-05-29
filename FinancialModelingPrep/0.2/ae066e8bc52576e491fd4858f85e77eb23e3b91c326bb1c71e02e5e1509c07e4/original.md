```
earnings_call_transcripts(fmp, symbol)
earnings_call_transcripts(fmp, symbol, year)
earnings_call_transcripts(fmp, symbol, year, quarter)
```

Returns earnings call transcripts for a specified symbols.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol or "all" if not provided.
  * `year::Integer`: A calendar year.
  * `quarter::Integer`: One of 1, 2, 3 or 4.

See [Earnings-Call-Transcript](https://site.financialmodelingprep.com/developer/docs/#Earning-Call-Transcript) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the available transcript dates for AAPL
data = earnings_call_transcripts(fmp, "AAPL")

# get the earnings call transcript for AAPL in Q3 of 2022
data = earnings_call_transcripts(fmp, "AAPL", year = 2022, quarter = 3)
```
