```
get_substruct_match(mol::Mol, qmol::Mol, options::Union{Dict{String,Any},Nothing}=nothing)::Dict{String, Any}
```

部分構造の一致を取得します。

```julia
pattern = get_qmol("ccO")
mol = get_mol("c1ccccc1O")
smatch = get_substruct_match(mol, pattern)
```
