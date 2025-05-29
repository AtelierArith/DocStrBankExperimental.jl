```
NanosecondDateTime(dt::DateTime)
```

`DateTime`から`NanosecondDateTime`を作成します、`dt`。

# 例

```
julia> using Dates

julia> dt = now()
2021-04-18T22:03:52.145

julia> ndt = NanosecondDateTime(dt)
NanosecondDateTime("2021-04-18T22:03:52.145000000")

julia> datetime(ndt) == dt
true
```
