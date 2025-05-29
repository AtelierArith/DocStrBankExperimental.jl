```
rand(::Type{Singleton}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### アルゴリズム

要素は平均0、標準偏差1の正規分布に従うベクトルです。
