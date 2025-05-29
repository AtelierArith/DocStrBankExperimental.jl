```
slice_graph(g::PeriodicGraph{D}, remove::Vector{<:Integer}) where D
```

`g` からオフセット `o` が `!iszero(o[remove])` であるすべてのエッジを削除することによって `PeriodicGraph{D}` を抽出します。

[`slice_graph(g::PeriodicGraph{D}, remove::Union{SVector{N},NTuple{N}}) where {D,N}`](@ref) メソッドとは異なり、エッジが削除される次元はここでは保持されます。

`remove` はソートされており、一意の要素を含むと仮定されます。

!!! warning
    前提条件の検証は行われません。

