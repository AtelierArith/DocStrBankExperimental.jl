```
get_rdkit_fp(mol::Mol, details::Union{Dict{String,Any},Nothing}=nothing)::String
```

RDKitフィンガープリントを取得します。

```julia
rfp = get_rdkit_fp(mol)
```
