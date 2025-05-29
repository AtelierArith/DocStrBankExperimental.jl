```
time_from_index(sample_rate, sample_range::AbstractUnitRange)
```

`sample_rate`がHzで与えられたとき、`sample_range`に対応する`TimeSpan`を返します。

返されるスパンは、最終サンプルとその後のサンプルの間の時間を含み、後者自体は含みません。

例:

```jldoctest
julia> time_from_index(100, 1:100)
TimeSpan(0 nanoseconds, 1000000000 nanoseconds)

julia> time_from_index(100, 101:101)
TimeSpan(1000000000 nanoseconds, 1000000001 nanoseconds)

julia> time_from_index(100, 301:600)
TimeSpan(3000000000 nanoseconds, 6000000000 nanoseconds)
```
