```
MMMBackground(median_factor=3, mean_factor=2)
```

背景を推定するために、`median_factor * median - mean_factor * mean` の形のモード推定器を使用します。このアルゴリズムは、元々DAOPHOTで実装された`MMMBackground`ルーチンに基づいています。`MMMBackground`はデフォルトで`median_factor=3`と`mean_factor=2`の因子を使用します。この推定器は、汚染された空のピクセル値が真の値から圧倒的に正の偏差を示すと仮定しています。

# 例

```jldoctest
julia> x = ones(3, 5);

julia> MMMBackground()(x)
1.0

julia> MMMBackground(median_factor=4, mean_factor=3)(x, dims = 1)
1×5 Matrix{Float64}:
 1.0  1.0  1.0  1.0  1.0
```

# 参照

  * [`SourceExtractorBackground`](@ref)
