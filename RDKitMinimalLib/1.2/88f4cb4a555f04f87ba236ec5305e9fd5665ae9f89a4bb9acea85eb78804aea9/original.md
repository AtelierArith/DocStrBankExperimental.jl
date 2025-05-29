```
get_substruct_match(mol::Mol, qmol::Mol, options::Union{Dict{String,Any},Nothing}=nothing)::Dict{String, Any}
```

Gets a substructure match.

```julia
pattern = get_qmol("ccO")
mol = get_mol("c1ccccc1O")
smatch = get_substruct_match(mol, pattern)
```
