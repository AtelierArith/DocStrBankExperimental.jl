```julia
add_residue!(
    topology::Chemfiles.Topology,
    residue::Chemfiles.Residue
)

```

Add a copy of `residue` to this `topology`.

The residue id must not already be in the topology, and the residue must contain only atoms that are not already in another residue.
