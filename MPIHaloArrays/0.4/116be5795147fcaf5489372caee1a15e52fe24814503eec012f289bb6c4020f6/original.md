Partition the array `A` on the rank `root` into chunks based on the given parallel toplogy. The array data in `A` does not have halo regions. The MPIHaloArray constructor adds the halo regions. This returns a `MPIHaloArray`

# Arguments

  * `A`: Global array to be split up into chunks and sent to all ranks. This does **not** include halo cells
  * `root`: MPI rank that `A` lives on
  * `nhalo`: Number of halo cells to create
  * `halo_dims`: Tuple of the dimensions that halo exchanges occur on (not fully working yet)
