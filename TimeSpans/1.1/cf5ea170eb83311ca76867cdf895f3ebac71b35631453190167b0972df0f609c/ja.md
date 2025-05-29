```
merge_spans!(predicate, spans)
```

可変でインデックス可能な時間範囲のイテレータと、2つの時間的に連続した時間範囲を比較する関数を与えると、`predicate` が `true` を返すすべてのペアが [`shortest_timespan_containing`](@ref) を介してマージされた状態で、ソートされた順序のイテレータを返します。

```jldoctest
julia> spans = [TimeSpan(0, 10), TimeSpan(6, 12), TimeSpan(15, 20),
                TimeSpan(21, 30), TimeSpan(29, 31)]
5-element Vector{TimeSpan}:
 TimeSpan(00:00:00.000000000, 00:00:00.000000010)
 TimeSpan(00:00:00.000000006, 00:00:00.000000012)
 TimeSpan(00:00:00.000000015, 00:00:00.000000020)
 TimeSpan(00:00:00.000000021, 00:00:00.000000030)
 TimeSpan(00:00:00.000000029, 00:00:00.000000031)

julia> merge_spans!(overlaps, spans)
3-element Vector{TimeSpan}:
 TimeSpan(00:00:00.000000000, 00:00:00.000000012)
 TimeSpan(00:00:00.000000015, 00:00:00.000000020)
 TimeSpan(00:00:00.000000021, 00:00:00.000000031)

julia> merge_spans!((a, b) -> start(b) - stop(a) < Nanosecond(5), spans)
1-element Vector{TimeSpan}:
 TimeSpan(00:00:00.000000000, 00:00:00.000000031)
```
