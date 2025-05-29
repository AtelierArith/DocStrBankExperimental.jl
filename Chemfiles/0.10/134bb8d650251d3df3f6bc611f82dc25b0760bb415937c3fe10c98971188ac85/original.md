```julia
set_topology!(
    trajectory::Chemfiles.Trajectory,
    topology::Chemfiles.Topology
)

```

Set the `Topology` associated with a `trajectory`. This topology will be used when reading and writing the file, replacing any topology in the file.
