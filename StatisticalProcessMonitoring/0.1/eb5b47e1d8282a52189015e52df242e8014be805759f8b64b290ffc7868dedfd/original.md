```
BlockBootstrap{T} <: AbstractSampling
```

Represents a (circular) block bootstrap sampling method.

# Fields

  * `block::T`: The current block of data being sampled from.
  * `blocksize::Int`: The size of each block.
  * `t::Int`: The current index within the block.

# Constructors

  * `BlockBootstrap(blocksize::Int, data::Vector{T}) where T`: Constructs a `BlockBootstrap` object for a vector of data.
  * `BlockBootstrap(blocksize::Int, data::Matrix{T}) where T`: Constructs a `BlockBootstrap` object for a matrix of data.
