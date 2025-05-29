# 拡張ヘルプ

```
rand(::Type{Star}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### アルゴリズム

述語 `P` を直接渡すことができます。`P` が `nothing`（デフォルト）の場合、次元 `dim` のランダムな `HPolytope` を生成します。

すべての数値は平均0、標準偏差1の正規分布に従います。
