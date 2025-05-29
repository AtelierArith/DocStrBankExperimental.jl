```
select_device()
```

Select the device (GPU) corresponding to the node-local MPI rank and return its ID.

!!! note "device indexing"
      * CUDA.jl device indexing is 0-based.
      * AMDGPU.jl device indexing is 1-based.
      * The returned ID is therefore 0-based for CUDA and 1-based for AMDGPU.


See also: [`init_global_grid`](@ref)
