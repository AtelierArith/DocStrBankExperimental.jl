```
merge_spans!(predicate, spans)
```

Given a mutable, indexable iterator of timespans and a function to compare two time-sequential timespans, return the iterator in sorted order with all pairs for which `predicate` returns `true` merged via [`shortest_timespan_containing`](@ref).

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
