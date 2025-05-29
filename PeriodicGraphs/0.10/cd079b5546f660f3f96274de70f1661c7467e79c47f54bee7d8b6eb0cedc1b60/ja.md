```
strong_rings([rs::Vector{Vector{Int}},] g::PeriodicGraph{D}, [depth::Integer=15,] symmetries::AbstractSymmetryGroup=NoSymmetryGroup(g), dist::DistanceRecord=DistanceRecord(g,depth)) where D
```

`g`の強いリングのリストを、長さ`2*depth+3`まで計算します。各リングは、その頂点の[`hash_position`](@ref)のリストで表されます。

オプションの最初の引数`rs`は、以前に計算された場合に提供できるリングのリストです。

他の引数の意味については、[`rings`](@ref)を参照してください。

強いリングとは、より小さなサイクルの和に分解できないグラフのサイクルです。対照的に、リングは2つの小さなサイクルの和に分解できないサイクルです。特に、すべての強いリングはリングです。

リングの頂点を表す整数のリストではなく、リングの辺を表す整数のリストとしてリングを取得するには、[`strong_erings`](@ref)も参照してください。
