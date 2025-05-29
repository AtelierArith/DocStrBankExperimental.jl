```
StationaryBootstrap{T} <: AbstractSampling
```

Represents a stationary block bootstrap sampling method, where the block length is sampled from a `Geometric` random variable.

# Fields

  * `block::T`: The current block of data being sampled from.
  * `blocksize::Int`: The average size of each block.
  * `t::Int`: The current index within the block.

# Constructors

  * `StationaryBootstrap(blocksize::Int, data::Vector{T}) where T`: Constructs a `StationaryBootstrap` object for a vector of data.
  * `StationaryBootstrap(blocksize::Int, data::Matrix{T}) where T`: Constructs a `StationaryBootstrap` object for a matrix of data.
