```
FieldArray
```

A generic [xarray](https://xarray.pydata.org/en/stable/index.html)-like or  [IRIS](https://scitools-iris.readthedocs.io/en/latest/)-like  n-dimensional Array with named dimensions and optional coordinates.

NB: this aims to be simple and generic, not efficient !!! Intended for representing model output, not for numerically-intensive calculations.

# Fields

  * `name::String`: variable name
  * `values::AbstractArray`: n-dimensional Array of values
  * `dims_coords::Vector{Pair{PALEOboxes.NamedDimension, Vector{PALEOmodel.FieldArray}}}`: Names of dimensions with optional attached coordinates
  * `attributes::Union{Nothing, Dict{Symbol, Any}}`: variable attributes
