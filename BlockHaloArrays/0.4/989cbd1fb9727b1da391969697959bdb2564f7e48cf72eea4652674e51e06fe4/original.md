Construct a BlockHaloArray

# Arguments

  * `dims::NTuple{N,Int}`: Array dimensions
  * `nhalo::Integer`: Number of halo entries (equal in all dimensions)

# Keyword Arguments

  * `nblocks::Integer`: Number of blocks to divide the array into; default is nthreads()
  * `T`:: Array number type; default is Float64
