```
VkFFTPlan{T}(app::Ptr{Cvoid}, config::Ptr{Cvoid}, direction::Int32, dims::NTuple{N, Int} where N, region, buffer_size::AbstractArray{Int}, type::DataType, is_inplace::Bool)
```

A struct that holds the plan for a VkFFT operation.

# Fields

  * `app::Ptr{Cvoid}`: The equivalent of an FFTW plan but for VkFFT
  * `config::Ptr{Cvoid}`: A struct that holds the VkFFFT configuration
  * `direction::Int32`: -1 for forward, 1 for inverse
  * `dims::NTuple{N, Int} where N`: The size of the input array
  * `region`: The dimensions on which to perform the FFT
  * `buffer_size::AbstractArray{Int}`: The size of the buffer VkFFT will use (in bytes)
  * `is_inplace::Bool`: Whether the plan is in-place (for optimization)
