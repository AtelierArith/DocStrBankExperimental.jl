```
ERA5Dummy(;
    path  :: AbstractString = homedir(),
) -> ERA5Dummy <: ERA5Dataset
```

A function that creates a dummy `ERA5Dataset` that contains only information on the path of the ERA5 LandSea mask

# Keyword Arguments

  * `path` : The specified directory in which to save the data
