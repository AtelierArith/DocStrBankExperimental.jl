A blocked array structure that stores thread-specific data in blocks. This facilitates a micro domain-decompisition for shared-memory applications. Each thread operates on it's own block of data. This provides better performance scaling than multi-threaded loops

# Fields

  * `blocks::Vector{AA}`:
  * `block_layout::NTuple{D,Int}`: number of blocks along each dimension
  * `global_blockranges::Array{NTuple{D,UnitRange{Int}},D}`: Indexing/ranges of each block from the global perspective
  * `nhalo::Int`: Number of halo regions, e.g. 2 entries along each dimension
  * `loop_limits::Vector{Vector{Int}}`: Looping limits for convienence e.g. `[ilo,ihi,jlo,jhi]`
  * `globaldims::NTuple{D,Int}`: Dimensions of the array if it were a simple `Array{T,D}`, e.g. `(20,20)`
