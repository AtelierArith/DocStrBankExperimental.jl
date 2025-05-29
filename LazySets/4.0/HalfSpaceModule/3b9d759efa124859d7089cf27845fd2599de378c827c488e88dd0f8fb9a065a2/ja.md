# 拡張ヘルプ

```
rand(::Type{HalfSpace}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### アルゴリズム

すべての数値は平均0、標準偏差1の正規分布に従います。さらに、制約 `a` はゼロではありません。
