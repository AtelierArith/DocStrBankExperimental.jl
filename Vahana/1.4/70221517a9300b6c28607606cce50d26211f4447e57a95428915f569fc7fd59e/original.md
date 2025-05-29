```
write_snapshot(sim::Simulation, [comment::String = ""; ignore = []])
```

Writes the current state of the simulation `sim` to the attached HDF5 file. `comment` can be used to identify the snapshot via [`list_snapshots`](@ref), and to read this snapshot via the [`read_snapshot!`](@ref) function by utilizing the `comment` keyword of this function.

`ignore` is a list of agent and/or edge types, that should not be written.

See also [`create_h5file!`](@ref), [`read_snapshot!`](@ref)
