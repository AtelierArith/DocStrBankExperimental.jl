```
abstract type DecodeOptions
```

Options for decoding data.

Properties are public for reading. All `DecodeOptions` have a keyword argument constructor that accept all properties as arguments. All `DecodeOptions` have a `codec::Codec` property.

Required methods for a type `T <: DecodeOptions` to implement:

  * `try_find_decoded_size(::T, src::AbstractVector{UInt8})::Union{Nothing, Int64}`
  * `try_decode!(::T, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}; kwargs...)::Union{Nothing, Int64}`

Optional methods to implement:

  * `is_thread_safe(::T)::Bool`: defaults to `false`.
  * `try_resize_decode!(::T, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}, max_size::Int64; kwargs...)::Union{Nothing, Int64}`: defaults to using `try_decode!` and `try_find_decoded_size`
