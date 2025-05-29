```julia
set_topology!(
    trajectory::Chemfiles.Trajectory,
    path::AbstractString
)
set_topology!(
    trajectory::Chemfiles.Trajectory,
    path::AbstractString,
    format::AbstractString
)

```

Set the `Topology` associated with a `trajectory` by reading the first frame of the file at `path`; and extracting the topology of this frame. The optional `format` parameter can be used to specify the file format.
