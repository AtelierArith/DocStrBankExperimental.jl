```
mergers_and_acquisitions_search(fmp, params...)
```

Returns a JSON table containing mergers and acquisitions search results.

# Arguments

  * `fmp::FMP`: A Financial Modeling Prep instance.
  * `params...`: Additional keyword query params.

See [Mergers-and-Acquisitions](https://site.financialmodelingprep.com/developer/docs/#MERGER-AND-ACQUISITION) for more details.

# Examples

```julia
# create a FMP API instance
fmp = FMP()

# search for mergers and acquisitions
data = mergers_and_acquisitions_search(fmp, name = "Syros")
```
