```
convert_to_inference_data(obj::NamedTuple; kwargs...) -> InferenceData
convert_to_inference_data(obj::Vector{Vector{<:NamedTuple}}; kwargs...) -> InferenceData
```

Convert `obj` to an [`InferenceData`](@ref). See [`from_namedtuple`](@ref) for a description of `obj` possibilities and `kwargs`.
