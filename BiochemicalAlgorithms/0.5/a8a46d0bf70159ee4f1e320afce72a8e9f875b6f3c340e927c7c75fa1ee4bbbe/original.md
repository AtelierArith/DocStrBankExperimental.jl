```
bonds(::ChainTable)
bonds(::FragmentTable)
bonds(::MoleculeTable)
```

Returns a `BondTable{T}` containing all bonds where at least one associated atom belongs to the given table.
