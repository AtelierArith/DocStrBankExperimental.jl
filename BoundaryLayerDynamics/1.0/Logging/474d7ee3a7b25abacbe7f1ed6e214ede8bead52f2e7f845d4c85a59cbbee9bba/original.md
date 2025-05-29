```
Snapshots(; kwargs...)
```

Save the instantaneous state $\mathbf{\hat{s}}$ to a collection of [Cartesian Binary Data](https://gitlab.com/efpl-columbia/codes/cbd-format) files at regular intervals during the simulation.

# Keywords

  * `frequency`: The frequency (in units of simulation time) at which snapshots should be saved. Note that this should be a multiple of the time step $Δt$.
  * `path = "output/snapshots"`: Path to a folder inside which the snapshots will be saved.
  * `centered = true`: Save values at the $x₁$- and $x₂$-locations at the center of the intervals obtained by dividing the domain into $N₁×N₂$ segments. If set to `false`, the locations start at 0 instead and end one grid spacing before the end of the domain.
  * `precision::DataType`: The floating-point data type used in the output, either `Float32` or `Float64`. By default this is set to the data type used for the simulation by the `Model`.
