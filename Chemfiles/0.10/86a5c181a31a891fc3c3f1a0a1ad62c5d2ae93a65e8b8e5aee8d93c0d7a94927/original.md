```julia
residue_for_atom(
    topology::Chemfiles.Topology,
    index::Integer
) -> Union{Nothing, Chemfiles.Residue}

```

Get a copy of the residue containing the atom at `index` in the `topology`.

This function will return `nothing` if the atom is not in a residue, or if the `index` is bigger than the number of atoms in the topology.
