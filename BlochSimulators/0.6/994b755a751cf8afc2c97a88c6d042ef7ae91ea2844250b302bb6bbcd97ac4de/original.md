```
simulate_magnetization(resource, sequence, parameters)
```

Simulate the magnetization response (typically the transverse magnetization at echo times without any spatial encoding gradients applied) for all combinations of tissue properties contained in `parameters`.

This function can also be used to generate dictionaries for MR Fingerprinting purposes.

# Arguments

  * `resource::AbstractResource`: Either `CPU1()`, `CPUThreads()`, `CPUProcesses()` or `CUDALibs()`
  * `sequence::BlochSimulator`: Custom sequence struct
  * `parameters::SimulationParameters`: Array with different combinations of tissue properties for each voxel.

# Note

  * If `resource == CUDALibs()`, the sequence and parameters must have been moved to the GPU using `gpu(sequence)` and `gpu(parameters)` prior to calling this function.
  * If `resource == CPUProcesses()`, the parameters must be a `DArray` with the first dimension corresponding to the number of workers. The function will distribute the simulation across the workers in the first dimension of the `DArray`.

# Returns

  * `magnetization::AbstractArray`: Array of size (output_size(sequence), length(parameters)) containing the magnetization response of the sequence for all combinations of input tissue properties.
