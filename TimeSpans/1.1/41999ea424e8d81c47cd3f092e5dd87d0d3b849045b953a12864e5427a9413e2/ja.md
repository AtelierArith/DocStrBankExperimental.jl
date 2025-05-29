```
time_from_index(sample_rate, sample_index)
```

`sample_rate`がHzであり、`sample_index > 0`を仮定すると、最も早い`ナノ秒`を返します。

例:

```jldoctest
julia> time_from_index(1, 1)
0 nanoseconds

julia> time_from_index(1, 2)
1000000000 nanoseconds

julia> time_from_index(100, 100)
990000000 nanoseconds

julia> time_from_index(100, 101)
1000000000 nanoseconds
```
