```julia
mutable struct Thin{T, O<:OnlineStatsBase.OnlineStat{T}} <: OnlineStatsBase.OnlineStat{T}
```

# Usage

```
Thin(b::Int, stat::OnlineStat)
```

Thins `stat` with an interval `b`, i.e. only passes every b-th observation to `stat`.
