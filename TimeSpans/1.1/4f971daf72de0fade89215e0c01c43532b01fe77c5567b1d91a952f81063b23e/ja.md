```
index_from_time(sample_rate, span)
```

`sample_rate`がHzで与えられたときに、`span`に対応するインデックスの`UnitRange`を返します：

```jldoctest
julia> index_from_time(100, TimeSpan(Second(0), Second(1)))
1:100

julia> index_from_time(100, TimeSpan(Second(1)))
101:101

julia> index_from_time(100, TimeSpan(Second(3), Second(6)))
301:600
```
