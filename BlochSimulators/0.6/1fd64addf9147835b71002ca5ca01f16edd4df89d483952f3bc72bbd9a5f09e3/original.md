```
simulate_signal(resource, sequence, parameters, trajectory, coil_sensitivities)
```

Simulate the MR signal at timepoint `t` from coil `i` as: `sᵢ(t) = ∑ⱼ cᵢⱼρⱼmⱼ(t)`, where `cᵢⱼ`is the coil sensitivity of coil `i` at position of voxel `j`, `ρⱼ` is the proton density of voxel `j` and `mⱼ(t)` the (normalized) transverse magnetization in voxel `j` obtained through Bloch simulations.

# Arguments

  * `resource::AbstractResource`: Either `CPU1()`, `CPUThreads()`, `CPUProcesses()` or `CUDALibs()`
  * `sequence::BlochSimulator`: Custom sequence struct
  * `parameters::SimulationParameters`: Array with tissue properties for each voxel
  * `trajectory::AbstractTrajectory`: Custom trajectory struct
  * `coordinates::StructArray{<:Coordinates}`: Array with spatial coordinates for each voxel
  * `coil_sensitivities::AbstractMatrix`: Sensitivity of coil `j` in voxel `v` is given by `coil_sensitivities[v,j]`

# Returns

  * `signal::AbstractArray{<:Complex}`: Simulated MR signal for the `sequence` and `trajectory`. The array is of size (# samples per readout, # readouts, # coils).
