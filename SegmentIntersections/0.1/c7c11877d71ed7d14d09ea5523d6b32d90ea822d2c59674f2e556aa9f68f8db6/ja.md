```
find_intersections(segments::Vector{Segment{T}}; tol=1e-9) where {T<:AbstractFloat}
```

セグメント間のすべての交差点をベントリー・オットマンアルゴリズムを使用して計算します。

すべての状況に対して機能するようにトレランス値を設定するのは難しいので、すべての交差点が見つからない場合は、値を調整してみてください。

# 例

```jldoctest
julia> segments = [Segment(0,0,5,5), Segment(0,5,5,0)];
julia> intersections = find_intersections(segments)
julia> [Point(2.5, 2.5)]
```
