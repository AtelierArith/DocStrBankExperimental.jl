```
rings(g::PeriodicGraph{D}, [depth::Integer=15,] symmetries::AbstractSymmetryGroup=NoSymmetryGroup(g), dist::DistanceRecord=DistanceRecord(g,depth)) where D
```

`g`のリングのリストを長さ`2*depth+3`まで計算します。各サブリストの要素の`reverse_hash_position`が頂点であるリングの`Vector{Int}`のリストを返します。また、返されたリングに作用する[`AbstractSymmetryGroup`](@ref)も返します。

リングは、サイクルの頂点間に、サイクル内の頂点を接続するパスよりも短いパスが存在しないグラフのサイクルです。

提供される場合、`symmetries`は、その文書化されたインターフェースを尊重する[`AbstractSymmetryGroup`](@ref)オブジェクトとしてグラフの対称性を表すべきです。

[`PeriodicGraphs.DistanceRecord`](@ref) `dist`は、グラフ内の頂点のペア間の距離を追跡するためにオプションで提供できます。
