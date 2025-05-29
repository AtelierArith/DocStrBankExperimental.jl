```
get_qmol(mol_string::AbstractString, details::Union{Dict{String,Any},Nothing}=nothing)::Union{Mol,Nothing}
```

Get a query mol (for substructure search) for a molblock (v2000, v3000), SMILES or SMARTS.

```julia
mol = get_qmol("c1ccccc1")
```
