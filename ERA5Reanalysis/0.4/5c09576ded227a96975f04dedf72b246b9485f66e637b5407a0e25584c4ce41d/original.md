```
addCDSAPIkey(
    key :: AbstractString;
    url :: AbstractString = "https://cds.climate.copernicus.eu/api/v2",
    filename  :: AbstractString = ".cdsapirc",
    overwrite :: Bool = false
) -> nothing
```

Adds the user's CDSAPI key to a file in the `homedir()` (by default specified as `.cdsapirc`)

## Arguments

  * `key` : The user's CDSAPI key

## Keyword Arguments

  * `url` : The user's CDSAPI key
  * `filename`  : The name of the file the url and key are saved to in the `homedir()`
  * `overwrite` : If `true` and if `filename` already exists, then overwrite
