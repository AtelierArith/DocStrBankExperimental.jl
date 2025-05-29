```julia
atoms(
    substruct::BiochemicalAlgorithms.Substructure{T, A} where A<:BiochemicalAlgorithms.AbstractAtomContainer{T};
    frame_id,
    molecule_idx,
    chain_idx,
    secondary_structure_idx,
    fragment_idx
) -> BiochemicalAlgorithms.SystemComponentTable{T, C} where {T, C<:BiochemicalAlgorithms.Atom{T}}

```

Returns an `AtomTable` for all of the given system's atoms matching the given criteria (value or `missing`). Fields given as `nothing` are ignored. The returned table contains all public and private atom fields.
