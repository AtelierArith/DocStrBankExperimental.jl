```
gainers(fmp)
```

Returns the biggest gainers.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.

See [Most-Gainer](https://site.financialmodelingprep.com/developer/docs/#Most-Gainer-Stock-Companies) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the biggest gainers
data = gainers(fmp)
```
