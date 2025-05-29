```
overlap_mesh(outfile::AbstractString, meshfile_a::AbstractString, meshfile_b::AbstractString; verbose=false)
```

Create the overlap mesh of `meshfile_a` and `meshfile_b` and write it to `outfile`. All files should be in Exodus format.

Set `verbose=true` to print information.

See [Tempest remap: mesh generation](https://github.com/ClimateGlobalChange/tempestremap/#mesh-generation)
