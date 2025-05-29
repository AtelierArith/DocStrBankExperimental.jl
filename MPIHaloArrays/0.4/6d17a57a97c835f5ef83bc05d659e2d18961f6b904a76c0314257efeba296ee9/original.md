MPIHaloArray constructor

# Arguments

  * `A`: AbstractArray{T,N}
  * `topo`: Parallel topology type, e.g. CartesianTopology
  * `nhalo`: Number of halo cells

# Keyword Arguments

  * `do_corners`: [true] Exchange corner halo regions
  * `com_model`: [:p2p] Communication model, e.g. :p2p is point-to-point (Isend, Irecv), :rma is onesided (Get,Put), :shared is MPI's shared memory model
