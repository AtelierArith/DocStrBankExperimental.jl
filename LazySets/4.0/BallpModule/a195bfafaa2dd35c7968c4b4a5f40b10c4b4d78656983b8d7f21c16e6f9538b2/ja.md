# 拡張ヘルプ

```
rand(::Type{Ballp}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### アルゴリズム

中心と半径は平均0、標準偏差1の正規分布に従います。さらに、半径は非負です。p-ノルムは、平均1、標準偏差1の正規分布に従う数 ≥ 1 です。
