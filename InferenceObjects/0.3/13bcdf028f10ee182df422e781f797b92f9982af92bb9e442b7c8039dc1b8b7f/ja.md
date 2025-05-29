```
convert_to_inference_data(obj::NamedTuple; kwargs...) -> InferenceData
convert_to_inference_data(obj::Vector{Vector{<:NamedTuple}}; kwargs...) -> InferenceData
```

`obj`を[`InferenceData`](@ref)に変換します。`obj`の可能性と`kwargs`の説明については、[`from_namedtuple`](@ref)を参照してください。
