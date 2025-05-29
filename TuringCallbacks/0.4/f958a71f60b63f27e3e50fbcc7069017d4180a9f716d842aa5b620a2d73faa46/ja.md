```julia
struct WindowStat{T, O} <: OnlineStatsBase.OnlineStat{T}
```

# 使用法

```
WindowStat(b::Int, stat::O) where {O <: OnlineStat}
```

`stat`を長さ`b`の`MovingWindow`に「ラップ」します。

`value(o::WindowStat)`は、`MovingWindow`に含まれるバッチデータのみに*フィット*した、`stat`と同じ型の`OnlineStat`を返します。
