```julia
Residue(
    topology::Chemfiles.Topology,
    index::Integer
) -> Chemfiles.Residue

```

Get a copy of the residue at `index` from a `topology`.

The residue index in the topology is not always the same as the residue identifier.
