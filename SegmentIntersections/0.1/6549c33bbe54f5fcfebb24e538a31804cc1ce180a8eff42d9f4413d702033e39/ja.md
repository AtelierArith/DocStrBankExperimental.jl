```
find_intersections_brute(segments::Vector{Segment{T}}) where {T<:AbstractFloat}
```

セグメント間のすべての交差点を計算します。これはO(n^2)のブルートフォースアルゴリズムです。このO(N^2)のブルートフォースバージョンでは、すべてのセグメントをすべてのセグメントと比較して交差点をテストします。この方法は、ポイントが少なく交差点が多い場合、Bentley-Ottman法よりも速くなります。

# 例

```jldoctest
julia> segments = [Segment(0,0,5,5), Segment(0,5,5,0)];
julia> intersections = find_intersections_brute(segments)
julia> [Point(2.5, 2.5)]
```
