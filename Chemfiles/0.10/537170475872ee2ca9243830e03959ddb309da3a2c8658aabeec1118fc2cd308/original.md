```julia
dihedrals(topology::Chemfiles.Topology) -> Matrix{UInt64}

```

Get the dihedral angles in the `topology`, in a `4 x dihedrals_count(topology)` array.
