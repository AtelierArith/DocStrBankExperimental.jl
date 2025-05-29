```julia
are_linked(
    topology::Chemfiles.Topology,
    first::Chemfiles.Residue,
    second::Chemfiles.Residue
) -> Bool

```

Check if the two residues `first` and `second` from the `topology` are linked together, *i.e.* if there is a bond between one atom in the first residue and one atom in the second one.
