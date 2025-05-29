```
setupGeoRegions(;
    path :: AbstractString = pwd(),
    overwrite :: Bool = false
) -> nothing
```

Setup the directory specified by `path` with files for custom `GeoRegion`s. If `overwrite = true`, then any preexisting files are overwritten.

# Keyword Arguments

  * `path` : The path where the template list of custom GeoRegions will be copied to.          Defaults to the current working directory `pwd()`.
  * `overwrite` : If template files exist in this folder, overwrite?
