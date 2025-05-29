```
toKwargs(value::AbstractImageReconstructionParameters; kwargs...)
```

Convert a `AbstractImageReconstructionParameters` to a `Dict{Symbol, Any}` of each property.

Optional keyword arguments:

  * flatten::Vector{DataType}: Types to flatten, per default only `AbstractImageReconstructionParameters` are flattened.
  * ignore::Vector{Symbol}: Properties to ignore.
  * default::Dict{Symbol, Any}: Default values for properties that are missing.
  * overwrite::Dict{Symbol, Any}: Overwrite values for properties.
