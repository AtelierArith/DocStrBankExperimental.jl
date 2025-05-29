```
tablePolyRegions(;
    path :: AbstractString = homedir(),
    custom :: Bool = true,
    srex :: Bool = false,
    ar6  :: Bool = false
) -> nothing
```

Display all available PolyRegions in tabular format.

# Keyword Arguments

  * `path` : The path where the list of custom PolyRegions will be retrieved from.          Defaults to the user's home directory `homedir()`.
  * `custom` : If `true`, display custom user-defined PolyRegions. Default is `true`.
  * `srex` : If `true`, display SREX predefined PolyRegions. Default is `true`.
  * `ar6` : If `true`, display IPCC AR6 predefined PolyRegions. Default is `true`.
