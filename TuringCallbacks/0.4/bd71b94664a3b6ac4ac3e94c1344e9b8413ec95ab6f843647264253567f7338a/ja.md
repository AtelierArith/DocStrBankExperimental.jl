```julia
mutable struct Skip{T, O<:OnlineStatsBase.OnlineStat{T}} <: OnlineStatsBase.OnlineStat{T}
```

# 使用法

```
Skip(b::Int, stat::OnlineStat)
```

最初の `b` 観測をスキップしてから、それらを `stat` に渡します。
