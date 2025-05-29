```
get_svg(mol::Mol, smatches::Vector, details::Dict=Dict{String,Any}())::String
```

複数の部分構造マッチを持つmolのSVG表現を取得します。

```julia
svg = get_svg(mol, get_substruct_matches(mol, query))
```
