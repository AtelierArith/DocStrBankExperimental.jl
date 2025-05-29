```
nanoseconds(dt::NanosecondDateTime) -> ::Dates.Nanosecond(n)
```

`dt`で表される日付と時刻のミリ秒解像度を超える追加のナノ秒数を返します。この値は常に正です。

# 例

```
julia> ndt = NanosecondDateTime("1990-01-02T00:11:22.123456789")
NanosecondDateTime("1990-01-02T00:11:22.123456789")

julia> nanoseconds(ndt)
456789 nanoseconds
```

参照: [`NanosecondDateTime`](@ref).
