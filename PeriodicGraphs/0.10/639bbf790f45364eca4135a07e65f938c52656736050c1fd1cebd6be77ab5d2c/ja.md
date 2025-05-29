```
slice_graph(g::PeriodicGraph{D}, remove::Union{SVector{N},NTuple{N}}) where {D,N}
```

`g`からオフセット`o`が`!iszero(o[remove])`であるすべてのエッジを削除し、結果として得られるオフセットを縮小することによって、`PeriodicGraph{D-N}`を抽出します。言い換えれば、`remove`にある次元を削除します。

同じ次元数を維持しながらエッジを削除するには、[`slice_graph(g, collect(remove))`](@ref slice_graph(g::PeriodicGraph{D}, remove::Vector{<:Integer}) where D)を使用してください。

`remove`はソートされており、一意の要素を含むと仮定されています。

!!! warning
    前述の仮定の検証は行われません。

