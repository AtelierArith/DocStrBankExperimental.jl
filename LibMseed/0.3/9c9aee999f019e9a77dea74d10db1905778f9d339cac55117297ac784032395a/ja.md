```
nearest_datetime(dt::NanosecondDateTime) -> ::Dates.DateTime
```

`dt`を最も近いミリ秒に丸めて、`DateTime`を返します。

# 例

```
julia> ndt = NanosecondDateTime("1999-12-31T23:59:59.9996")
NanosecondDateTime("1999-12-31T23:59:59.999600000")

julia> nearest_datetime(ndt)
2000-01-01T00:00:00
```

参照: [`datetime`](@ref).
