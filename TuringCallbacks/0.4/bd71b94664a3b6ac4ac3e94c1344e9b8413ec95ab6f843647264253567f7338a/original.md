```julia
mutable struct Skip{T, O<:OnlineStatsBase.OnlineStat{T}} <: OnlineStatsBase.OnlineStat{T}
```

# Usage

```
Skip(b::Int, stat::OnlineStat)
```

Skips the first `b` observations before passing them on to `stat`.
