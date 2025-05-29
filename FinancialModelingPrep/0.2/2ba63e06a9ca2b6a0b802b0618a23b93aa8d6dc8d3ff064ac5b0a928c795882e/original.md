```
revenue_segments(fmp, symbol, segment = REVENUE_SEGMENTS.product, params...)
```

Returns a JSON table with the revenue segments for the specified symbol.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `segment::String`: A `REVENUE_SEGMENTS` option.
  * `params...`: Additional keyword query params.

See [Sales-Revenue-By-Segments](https://site.financialmodelingprep.com/developer/docs/#Sales-Revenue-By-Segments) for more details.
See [Revenue-Geographic-by-Segments](https://site.financialmodelingprep.com/developer/docs/#Revenue-Geographic-by-Segments) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get all yearly geographic revenue segments for AAPL
data = revenue_segments(fmp, "AAPL", segment = REVENUE_SEGMENTS.geographic, structure = "flat")

# get all quarterly product revenue segments for AAPL
data = revenue_segments(fmp, "AAPL", segment = REVENUE_SEGMENTS.product, period = "quarter", structure = "flat")
```
