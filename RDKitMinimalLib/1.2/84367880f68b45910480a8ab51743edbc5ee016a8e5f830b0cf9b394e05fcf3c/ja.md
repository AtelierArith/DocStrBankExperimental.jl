```
get_qmol(mol_string::AbstractString, details::Union{Dict{String,Any},Nothing}=nothing)::Union{Mol,Nothing}
```

モルブロック（v2000、v3000）、SMILES、またはSMARTSのためのクエリモル（部分構造検索用）を取得します。

```julia
mol = get_qmol("c1ccccc1")
```
