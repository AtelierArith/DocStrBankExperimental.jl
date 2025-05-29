```
remap_weights(
    weightfile::AbstractString,
    meshfile_in::AbstractString,
    meshfile_out::AbstractString,
    meshfile_overlap::AbstractString;
    verbose=false,
    kwargs...
)
```

Create a file `weightfile` in SCRIP format containing the remapping weights from `meshfile_in` to `meshfile_out`, where `meshfile_overlap` is constructed via [`overlap_mesh`](@ref).

Keyword arguments are passed as command-line options. These include:

  * `in_type` / `out_type`: the type of the input and output mesh:

      * `"fv"` (default): finite volume (one value per element)
      * `"cgll"`: continuous GLL finite element method (a single value for colocated nodes)
      * `"dgll"`: discontinuous GLL finite element method (duplicate values for colocated nodes)
  * 'in*np'/'out*np': Order of input and output meshes
  * 'mono': Monotonicity of remapping

Set `mono = true` for monotone remapping Set `verbose=true` to print information.

See [Tempest remap: offline map generation](https://github.com/ClimateGlobalChange/tempestremap/#offline-map-generation)
