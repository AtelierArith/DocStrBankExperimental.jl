```
RTree{T,N}([K], V; kwargs...) where {T,N,V}
```

`N`次元の[`RTree`](@ref)オブジェクトを構築し、[`SpatialElem{T,N,K,V}`](@ref `SpatialElem`)要素を格納します。`K`（空間要素識別子の型）が指定されていない場合、格納される要素にはIDがありません。
