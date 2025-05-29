```
add_arrays_data!(
    model, modeldata, arrays_eltype::DataType, arrays_tagname::AbstractString;
    [method_barrier=nothing] [, generated_dispatch=true] [, kwargs...])
```

Add a data array set to `modeldata`, allocate memory, and initialize reactiondata.

Element type and tag name are set by `arrays_eltype`, `arrays_tagname`

See [`allocate_variables!(model::Model, modeldata::AbstractModelData, arrays_idx::Int)`](@ref) and  [`initialize_reactiondata!`] for keyword arguments.
