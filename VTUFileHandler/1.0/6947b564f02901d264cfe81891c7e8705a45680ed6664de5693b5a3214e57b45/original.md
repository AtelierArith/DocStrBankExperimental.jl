```
VTUHeader(::Type{T},input::Vector{UInt8}) where {T<:Union{UInt32,UInt64}}
```

Computes the VTUHeader based on the headertype and a Base64 decoded input data array.

# Constructor

  * `::Type{T}`: headertype, either UInt32 or UInt64
  * `input::Vector{UInt8}`: input data

# Fields

  * `num_blocks::T` : number of blocks
  * `blocksize::T` : size of blocks
  * `last_blocksize::T` : size of last block (can be different)
  * `compressed_blocksizes::T` : size of compressed blocks
