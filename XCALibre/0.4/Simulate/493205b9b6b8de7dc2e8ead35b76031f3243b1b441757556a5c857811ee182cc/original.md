```
hardware = set_hardware(backend, workgroup)
```

Function used to configure the backend.

# Inputs

  * `backend` named tuple used to specify the backend e.g. `CPU()`, `CUDABackend()` or other backends supported by `KernelAbstraction.jl`
  * `workgroup::Int` this is an integer specifying the number of workers that cooperate in a parallel run. For GPUs this could be set to the size of the device's warp e.g. `workgroup = 32`. On CPUs, the default value in `KernelAbstractions.jl` is currently `workgroup = 1024`.

# Output

This function returns a `NamedTuple` with the fields `backend` and `workgroup` which are accessed by internally in `XCALibre.jl` to execute a given kernel.
