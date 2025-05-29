```
get_inchi(mol::Mol, details::Union{Dict{String,Any},Nothing}=nothing)::String
```

molオブジェクトのInChIを取得します。

```julia
inchi = get_inchi(mol)
```
