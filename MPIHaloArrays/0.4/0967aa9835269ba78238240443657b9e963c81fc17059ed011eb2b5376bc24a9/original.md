MPIHaloArray

# Fields

  * `data`: AbstractArray{T,N} - contains the local data on the current rank
  * `partitioning`: partitioning datatype
  * `comm`: MPI communicator
  * `window`: MPI window
  * `neighbor_ranks` : Vector{Int} - IDs of the neighboring arrays/MPI procs
  * `coords` : Vector{Int} - Coordinates in the global MPI space
  * `rank`: Current MPI rank
