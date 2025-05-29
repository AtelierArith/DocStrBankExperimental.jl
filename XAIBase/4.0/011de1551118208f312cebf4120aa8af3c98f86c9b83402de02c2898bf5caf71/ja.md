```
TopNFeatures(n)
```

上位nの特徴を選択します。

畳み込み層の出力に対しては、各特徴の高さと幅のチャネルにわたって関連性が合計されます。

[`IndexedFeatures`](@ref)も参照してください。

## 注意

XAIBaseインターフェースは、特徴が2次元または4次元（`(features, batchsize)`または`(width, height, features, batchsize)`）であると仮定しています。

また、バッチ次元が特徴の最後の次元であると仮定しています。

## 例

```julia-repl
julia> feature_selector = TopNFeatures(2)
 TopNFeatures(2)

julia> feature = rand(3, 2)
3×2 Matrix{Float64}:
 0.265312  0.953689
 0.674377  0.172154
 0.649722  0.570809

julia> feature_selector(feature)
2-element Vector{Vector{CartesianIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}}}:
 [CartesianIndices((2:2, 1:1)), CartesianIndices((1:1, 2:2))]
 [CartesianIndices((3:3, 1:1)), CartesianIndices((3:3, 2:2))]

julia> feature = rand(3, 3, 3, 2);

julia> feature_selector(feature)
2-element Vector{Vector{CartesianIndices{4, NTuple{4, UnitRange{Int64}}}}}:
 [CartesianIndices((1:3, 1:3, 2:2, 1:1)), CartesianIndices((1:3, 1:3, 1:1, 2:2))]
 [CartesianIndices((1:3, 1:3, 1:1, 1:1)), CartesianIndices((1:3, 1:3, 3:3, 2:2))]
```
