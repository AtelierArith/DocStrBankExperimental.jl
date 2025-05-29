```
abstract type EncodeOptions
```

Options for encoding data.

Properties are public for reading. All `EncodeOptions` have a keyword argument constructor that accept all properties as arguments. All `EncodeOptions` have a `codec::Codec` property.

Required methods for a type `T <: EncodeOptions` to implement:

  * `decoded_size_range(::T)::StepRange{Int64, Int64}`
  * `encode_bound(::T, src_size::Int64)::Int64`
  * `try_encode!(::T, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}; kwargs...)::Union{Nothing, Int64}`

Optional methods to implement:

  * `is_thread_safe(::T)::Bool`: defaults to `false`.
