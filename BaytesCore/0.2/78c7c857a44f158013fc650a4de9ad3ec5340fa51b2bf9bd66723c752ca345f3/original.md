```julia
struct SubSampled <: BaytesCore.DataStructure
```

Determines whether data can be subsampled for inference.

# Fields

  * `buffer::Vector{Int64}`: Buffer index for subsampled indices.
