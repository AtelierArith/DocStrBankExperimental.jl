```julia
struct WindowStat{T, O} <: OnlineStatsBase.OnlineStat{T}
```

# Usage

```
WindowStat(b::Int, stat::O) where {O <: OnlineStat}
```

"Wraps" `stat` in a `MovingWindow` of length `b`.

`value(o::WindowStat)` will then return an `OnlineStat` of the same type as  `stat`, which is *only* fitted on the batched data contained in the `MovingWindow`.
