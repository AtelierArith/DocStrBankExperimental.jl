```
datetime(dt::NanosecondDateTime) -> ::Dates.DateTime
```

`dt`の日時を返し、最も近いミリ秒に切り捨てます。完全な精度の時間を得るために、[`nanoseconds`](@ref LibMseed.nanoseconds)の数を加えます。

# 例

```
julia> ndt = NanosecondDateTime("2000-01-01T01:23:45.999999999")
NanosecondDateTime("2000-01-01T01:23:45.999999999")

julia> datetime(ndt)
2000-01-01T01:23:45.999
```

参照: [`NanosecondDateTime`](@ref), [`nearest_datetime`](@ref).
