```
magnetization_to_signal(resource, magnetization, parameters, trajectory, coordinates, coil_sensitivities)
```

Allocates memory for the signal and computes the signal for each coil separately using the `_signal_per_coil!` function.

# Implementation details

The `_signal_per_coil!` function has different implementations depending on the computational resources (i.e. the type of `resource`). The default implementations loop over all time points and compute the volume integral of the transverse magnetization in each voxel for each time point separately. This loop order is not necessarily optimal (and performance may be) across all trajectories and computational resources. If a better implementation is available, add new methods to this function for those specific combinations of resources and trajectories.

The "voxels" are assumed to be distributed over the workers. Each worker computes performs a volume integral over the voxels that it owns only (for all time points) using the CPU1() code. The results are then summed up across all workers.

# Note

When using multiple CPU's, the "voxels" are distributed over the workers. Each worker computes the signal for its own voxels in parallel and the results are summed up across all workers.
