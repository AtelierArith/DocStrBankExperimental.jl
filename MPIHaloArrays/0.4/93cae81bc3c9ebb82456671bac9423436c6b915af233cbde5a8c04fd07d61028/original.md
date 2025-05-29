CartesianTopology

The CartesianTopology type holds neighbor information, current rank, etc.

# Fields

  * `comm`: MPI commicator object
  * `nprocs`: Number of total processors (global)
  * `rank`: Current rank
  * `coords`: Coordinates in the global space, i.e. `(0,1,1)`
  * `global_dims`: Dimensions of the global domain, i.e. `(4,4)` is a 4x4 global domain
  * `isperiodic`: Vector{Bool}; Perodicity of each dimension, i.e. `(false, true, true)` means y and z are periodic
  * `neighbors`: OffsetArray{Int}; Neighbor ranks (including corners), indexed as `[[ilo, center, ihi], i, j, k]`
