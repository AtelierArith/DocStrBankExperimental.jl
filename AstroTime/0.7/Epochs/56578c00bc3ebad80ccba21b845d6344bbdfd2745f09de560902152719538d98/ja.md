```
now(::Type{Epoch})
now(::Type{Epoch{S}}) where S<:TimeScale
```

現在の日付と時刻を `Epoch` として取得します。デフォルトの時間スケールは TAI です。

# 例

```julia-repl
julia> now(Epoch)
2021-04-11T13:20:29.160 TAI

julia> now(TDBEpoch)
2021-04-11T13:21:21.518 TDB
```
