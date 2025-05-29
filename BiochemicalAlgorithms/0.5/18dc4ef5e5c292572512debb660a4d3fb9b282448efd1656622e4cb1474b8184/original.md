```
fragments(::SecondaryStructureTable)
fragments(::ChainTable)
fragments(::MoleculeTable)
```

Returns a `FragmentTable{T}` containing all fragments of the given table.

# Supported keyword arguments

  * `variant::Union{Nothing, FragmentVariantType} = nothing` Any value other than `nothing` limits the results to the matching variant type.
