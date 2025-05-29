```julia
MemoryTrajectory(
    format::AbstractString
) -> Chemfiles.Trajectory
MemoryTrajectory(
    format::AbstractString,
    data::Union{Nothing, AbstractString, Vector{UInt8}}
) -> Chemfiles.Trajectory

```

Open a trajectory that read in-memory data as if it were a formatted file.

The `format` of the data is mandatory, and must match one of the known formats. If `data` is `nothing`, this function creates a memory writer, the resulting data can be retrieved with `buffer`. Else, this function creates a memory reader using the given data.
