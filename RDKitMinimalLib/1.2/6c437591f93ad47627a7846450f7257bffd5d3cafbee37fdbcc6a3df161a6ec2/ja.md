```
get_json(mol::Mol, details::Union{Dict{String,Any},Nothing}=nothing)::String
```

molオブジェクトのjson（CommonChem形式）を取得します。

```julia
json = get_json(mol)
```
