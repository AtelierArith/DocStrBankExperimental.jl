```
TRMMDummy(
    ST = String;
    path  :: AbstractString = homedir(),
) -> npd :: IMERGDummy
```

Creates a `TRMMDummy` dataset `npd` that contains information on the data and mask paths

# Keyword Arguments

  * `path` : The directory in which the folder `trmmmask` will be created for the TRMM Land-Sea mask
