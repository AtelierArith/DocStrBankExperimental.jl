```julia
bonds(topology::Chemfiles.Topology) -> Matrix{UInt64}

```

Get the bonds in the `topology`, in a `2 x bonds_count(topology)` array.
