```
index_from_time(sample_rate, sample_time::Period)
```

`sample_rate`がHzであるとき、`sample_time`で取得した最も最近のサンプルの整数インデックスを返します。`sample_time`は非負であり、`convert(Nanosecond, sample_time)`をサポートしている必要があります。

例:

```jldoctest
julia> index_from_time(1, Second(0))
1

julia> index_from_time(1, Second(1))
2

julia> index_from_time(100, Millisecond(999))
100

julia> index_from_time(100, Millisecond(1000))
101
```
