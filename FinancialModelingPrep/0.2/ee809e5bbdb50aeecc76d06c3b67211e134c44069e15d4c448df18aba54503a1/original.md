```
press_releases(fmp, symbol, params...)
```

Returns stock press releases.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `symbol::String`: A stock symbol.
  * `params...`: Additional keyword query params.

See [Press-Releases](https://site.financialmodelingprep.com/developer/docs/#Press-Releases) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get first page of press releases from AAPL
data = press_releases(fmp, symbol = "AAPL", page = 0)
```
