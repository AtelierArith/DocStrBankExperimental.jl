```
sector_pe_ratios(fmp, params...)
```

Returns sector pe ratios.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Sectors-PE-Ratio](https://site.financialmodelingprep.com/developer/docs/#Sectors-PE-Ratio) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# get the sector PE ratios of the NYSE on Jan 1, 2023
data = sector_pe_ratios(fmp, date = "2023-01-01", exchange = "NYSE")
```
