```
industry_pe_ratios(fmp, params...)
```

Returns industry pe ratios.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Industries-PE-Ratio](https://site.financialmodelingprep.com/developer/docs/#Industries-PE-Ratio) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the industry PE ratios of the NYSE on Jan 1, 2023
data = industry_pe_ratios(fmp, date = "2023-01-01", exchange = "NYSE")
```
