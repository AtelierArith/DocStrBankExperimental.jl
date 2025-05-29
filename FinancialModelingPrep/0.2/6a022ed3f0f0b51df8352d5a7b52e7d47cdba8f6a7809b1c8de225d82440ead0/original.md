```
price_targets_by_analyst(fmp, name)
```

Returns price targets  from the specified name.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `name::String`: An analyst name.

See [Price-Target-by-Analyst-Name](https://site.financialmodelingprep.com/developer/docs/#Price-Target-By-Analyst-Name) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the price targets from Tim Anderson
data = price_targets_by_analyst(fmp, name = "Tim%20Anderson")
```
