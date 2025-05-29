```
namedtuple_to_dataset(data; kwargs...) -> Dataset
```

Convert `NamedTuple` mapping variable names to arrays to a [`Dataset`](@ref).

Any non-array values will be converted to a 0-dimensional array.

# Keywords

  * `attrs::AbstractDict{<:AbstractString}`: a collection of metadata to attach to the dataset, in addition to defaults. Values should be JSON serializable.
  * `library::Union{String,Module}`: library used for performing inference. Will be attached to the `attrs` metadata.
  * `dims`: a collection mapping variable names to collections of objects containing dimension names. Acceptable such objects are:

      * `Symbol`: dimension name
      * `Type{<:DimensionsionalData.Dimension}`: dimension type
      * `DimensionsionalData.Dimension`: dimension, potentially with indices
      * `Nothing`: no dimension name provided, dimension name is automatically generated
  * `coords`: a collection indexable by dimension name specifying the indices of the given dimension. If indices for a dimension in `dims` are provided, they are used even if the dimension contains its own indices. If a dimension is missing, its indices are automatically generated.
