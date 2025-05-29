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

指定された条件（値または `missing`）に一致するシステムのすべての原子のための `AtomTable` を返します。 `nothing` として与えられたフィールドは無視されます。返されるテーブルには、すべての公開および非公開の原子フィールドが含まれています。
