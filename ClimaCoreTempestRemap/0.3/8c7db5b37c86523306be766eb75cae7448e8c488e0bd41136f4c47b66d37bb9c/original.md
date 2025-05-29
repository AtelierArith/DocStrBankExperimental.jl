```
apply_remap(outfile::AbstractString, infile::AbstractString, weightfile::AbstractString, vars; verbose=false)
```

Remap the NetCDF file `infile` to `outfile`, using the remapping weights `weightfile` constructed via [`remap_weights`](@ref). `vars` should be a collection of variable names to remap.

Set `verbose=true` to print information.

See [Tempest remap: offline map application](https://github.com/ClimateGlobalChange/tempestremap/#offline-map-application)
