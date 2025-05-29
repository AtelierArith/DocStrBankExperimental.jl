```
ModelData(model::Model; arrays_eltype::DataType=Float64, allocatenans::Bool=true)
```

Create a ModelData struct containing `model` data arrays.

One set of data arrays is created with `eltype=arrays_eltype`, accessed with `arrays_idx=1`

Additional sets of data arrays may be added by [`push_arrays_data!`](@ref), eg in order to support automatic differentiation which requires Dual numbers as the array element type.

# Fields

  * `cellranges_all::Vector{AbstractCellRange}`: default cellranges covering all domains
  * `dispatchlists_all`: default dispatchlists covering all domains
  * `solver_view_all`: optional untyped context field for use by external solvers.
