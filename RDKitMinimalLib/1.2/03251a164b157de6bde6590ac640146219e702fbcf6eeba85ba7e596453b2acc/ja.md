```
get_mol(mol_string::AbstractString, details::Union{Dict{String,Any},Nothing}=nothing)::Union{Mol,Nothing}
```

モルブロック（v2000、v3000）、SMILES、またはSMARTSからモルを取得します。

```julia
mol = get_mol("CC(=O)Oc1ccccc1C(=O)O")
```
