```
InferenceData{group_names,group_types}
```

Container for inference data storage using DimensionalData.

This object implements the [InferenceData schema](@extref arviz schema).

Internally, groups are stored in a `NamedTuple`, which can be accessed using `parent(::InferenceData)`.

# Constructors

```
InferenceData(groups::NamedTuple)
InferenceData(; groups...)
```

Construct an inference data from either a `NamedTuple` or keyword arguments of groups.

Groups must be [`Dataset`](@ref) objects.

Instead of directly creating an [`InferenceData`](@ref), use the exported `from_xyz` functions or [`convert_to_inference_data`](@ref).
