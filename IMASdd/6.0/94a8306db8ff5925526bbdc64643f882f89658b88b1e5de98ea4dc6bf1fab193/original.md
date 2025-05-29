```
imas2hdf(@nospecialize(ids::Union{IDS,IDSvector}), filename::AbstractString;
         mode::String="w", target_group::String="/", overwrite::Bool=false,
         freeze::Bool=false, strict::Bool=false, desc::String="", kw...)
```

Save an IMAS data structure to an OMAS HDF5 file.

Arguments:

  * `filename`: HDF5 file path
  * `mode`: File open mode ("w", "a", or "r+"); "a" is converted to "r+"
  * `target_group`: Group where data will be stored (default is `"/"`)
  * `overwrite`: If true, overwrite the target group if it exists
  * `show_warnings`: If true, display warn messages
  * `freeze` evaluates expressions
  * `strict` dumps fields that are strictly in ITER IMAS only
  * `desc`: description of additional information (e.g., Shot number)
  * `compress`: compression level, an integer between 0 (no compression) and 9 (highest)
  * `kw...`: Options passed to the internal dispatch

Returns:

The result of `imas2hdf(ids, gparent; freeze, strict, desc)`.
