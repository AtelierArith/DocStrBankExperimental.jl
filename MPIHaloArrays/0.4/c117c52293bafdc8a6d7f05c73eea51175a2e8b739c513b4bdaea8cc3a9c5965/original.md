Gather all `MPIHaloArray`s onto the `root` MPI rank and stitch together. This will ignore halo region data and create a `Array` that represents the global state.

# Arguments

  * `A`: MPIHaloArray
  * `root`: MPI rank to gather `A` to
  * `halo_dims`: Tuple of the dimensions that halo exchanges occur on (not fully working yet)
