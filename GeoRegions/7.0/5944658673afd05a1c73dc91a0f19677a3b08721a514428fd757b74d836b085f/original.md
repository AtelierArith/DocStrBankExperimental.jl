```
tableRectRegions(;
    path :: AbstractString = homedir(),
    custom :: Bool = true,
    giorgi :: Bool = false
) -> nothing
```

Display all available RectRegions in tabular format.

# Keyword Arguments

  * `path` : The path where the list of custom RectRegions will be retrieved from.          Defaults to the user's home directory `homedir()`.
  * `custom` : If `true`, display custom user-defined RectRegions. Default is `true`.
  * `giorgi` : If `true`, display GF predefined RectRegions. Default is `true`.
