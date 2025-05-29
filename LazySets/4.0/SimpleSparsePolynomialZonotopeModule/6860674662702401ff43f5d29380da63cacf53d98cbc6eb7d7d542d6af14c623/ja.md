# 拡張ヘルプ

```
rand(::Type{SimpleSparsePolynomialZonotope};
     [N]::Type{<:Real}=Float64, [dim]::Int=2, [nparams]::Int=2,
     [maxdeg]::Int=3, [num_generators]::Int=-1,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### アルゴリズム

すべての数値は平均0、標準偏差1の正規分布に従います。

生成器の数は引数`num_generators`で制御できます。負の値の場合、範囲`dim:2*dim`内のランダムな数を選択します（ただし、`dim == 1`の場合は単一の生成器のみを作成します）。冗長な単項式が生成されると、最終的な生成器の数は少なくなる可能性があることに注意してください。
