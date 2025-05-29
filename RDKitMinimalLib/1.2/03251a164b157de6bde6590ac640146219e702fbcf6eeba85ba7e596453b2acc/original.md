```
get_mol(mol_string::AbstractString, details::Union{Dict{String,Any},Nothing}=nothing)::Union{Mol,Nothing}
```

Get a mol from a molblock (v2000, v3000), SMILES or SMARTS.

```julia
mol = get_mol("CC(=O)Oc1ccccc1C(=O)O")
```
