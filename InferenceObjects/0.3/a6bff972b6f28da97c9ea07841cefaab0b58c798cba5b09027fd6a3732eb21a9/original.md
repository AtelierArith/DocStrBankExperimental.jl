```
convert_to_inference_data(obj; group, kwargs...) -> InferenceData
```

Convert a supported object to an [`InferenceData`](@ref) object.

If `obj` converts to a single dataset, `group` specifies which dataset in the resulting `InferenceData` that is.

See [`convert_to_dataset`](@ref)

# Arguments

  * `obj` can be many objects. Basic supported types are:

      * [`InferenceData`](@ref): return unchanged
      * [`Dataset`](@ref)/`DimensionalData.AbstractDimStack`: add to `InferenceData` as the only group
      * `NamedTuple`/`AbstractDict`: create a `Dataset` as the only group
      * `AbstractArray{<:Real}`: create a `Dataset` as the only group, given an arbitrary name, if the name is not set

More specific types may be documented separately.

# Keywords

  * `group::Symbol = :posterior`: If `obj` converts to a single dataset, assign the resulting dataset to this group.
  * `dims`: a collection mapping variable names to collections of objects containing dimension names. Acceptable such objects are:

      * `Symbol`: dimension name
      * `Type{<:DimensionsionalData.Dimension}`: dimension type
      * `DimensionsionalData.Dimension`: dimension, potentially with indices
      * `Nothing`: no dimension name provided, dimension name is automatically generated
  * `coords`: a collection indexable by dimension name specifying the indices of the given dimension. If indices for a dimension in `dims` are provided, they are used even if the dimension contains its own indices. If a dimension is missing, its indices are automatically generated.
  * `kwargs`: remaining keywords forwarded to converter functions
