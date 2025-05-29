```
losers(fmp)
```

Returns the biggest losers.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Most-Loser](https://site.financialmodelingprep.com/developer/docs/#Most-Loser-Stock-Companies) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the biggest losers
data = losers(fmp)
```
