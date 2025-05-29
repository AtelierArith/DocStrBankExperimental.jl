# 拡張ヘルプ

```
rand(::Type{HPolyhedron}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### アルゴリズム

まずランダムな多面体を作成し、その後各制約についてランダムに（50%）含めるかどうかを決定します。
