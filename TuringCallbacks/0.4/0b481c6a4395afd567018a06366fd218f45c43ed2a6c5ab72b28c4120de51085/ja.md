```julia
mutable struct Thin{T, O<:OnlineStatsBase.OnlineStat{T}} <: OnlineStatsBase.OnlineStat{T}
```

# 使用法

```
Thin(b::Int, stat::OnlineStat)
```

`stat`を間隔`b`で薄くします。つまり、`stat`に対してはb番目の観測値のみを渡します。
