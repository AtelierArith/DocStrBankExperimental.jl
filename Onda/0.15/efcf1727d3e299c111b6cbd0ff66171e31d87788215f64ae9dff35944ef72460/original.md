```
format(file_format::AbstractString, info; kwargs...)
```

Return `f(info; kwargs...)` where `f` constructs the `AbstractLPCMFormat` instance that corresponds to `file_format` and info is a [`SamplesInfoV2`](@ref)-compliant value. `f` is determined by matching `file_format` to a suitable format constuctor registered via [`register_lpcm_format!`](@ref).

See also: [`deserialize_lpcm`](@ref), [`serialize_lpcm`](@ref)
