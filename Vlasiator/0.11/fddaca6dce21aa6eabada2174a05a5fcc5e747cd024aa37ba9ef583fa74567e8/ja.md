```
refineslice(meta, idlist::Vector{Int}, data::AbstractVector, normal::Symbol) -> Vector
refineslice(meta, idlist::Vector{Int}, data::AbstractMatrix, normal::Symbol) -> Matrix
refineslice(meta, idlist::Vector{Int}, data::AbstractArray, dir::Int)
```

セルID `idlist` と変数 `data` に基づいて、法線に垂直なスライス上で最も細かい細分化レベルのデータを生成します。`data` が2Dの場合、最初の次元はベクトル成分として扱われます。
