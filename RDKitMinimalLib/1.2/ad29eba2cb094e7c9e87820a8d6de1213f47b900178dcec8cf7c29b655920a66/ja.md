```
get_substruct_matches(mol::Mol, qmol::Mol, options::Union{Dict{String,Any},Nothing}=nothing)::Dict{String, Any}
```

すべての部分構造マッチを取得します。

```julia
pattern = get_qmol("ccO")
mol = get_mol("c1ccccc1O")
smatches = get_substruct_matches(mol, pattern)
```
