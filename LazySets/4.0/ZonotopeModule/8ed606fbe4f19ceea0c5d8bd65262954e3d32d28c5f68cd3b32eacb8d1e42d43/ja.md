# 拡張ヘルプ

```
rand(::Type{Zonotope}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### アルゴリズム

すべての数値は平均0、標準偏差1の正規分布に従います。

生成器の数は引数 `num_generators` で制御できます。負の値の場合、範囲 `dim:2*dim` の中からランダムな数を選択します（ただし `dim == 1` の場合は、単一の生成器のみを作成します）。
