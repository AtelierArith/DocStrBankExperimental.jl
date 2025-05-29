```
IndexedFeatures(indices...)
```

インデックスによって特徴を選択します。

畳み込み層の出力に対して、インデックスは特徴次元を指します。

関連情報 [`TopNFeatures`](@ref) を参照してください。

## 注意

XAIBase インターフェースは、特徴が 2 次元または 4 次元 (`(features, batchsize)` または `(width, height, features, batchsize)`) であると仮定しています。

また、バッチ次元が特徴の最後の次元であると仮定しています。

## 例

```julia-repl
julia> feature_selector = IndexedFeatures(2, 3)
 IndexedFeatures(2, 3)

julia> feature = rand(3, 3, 3, 2);

julia> feature_selector(feature)
2-element Vector{Vector{CartesianIndices{4, NTuple{4, UnitRange{Int64}}}}}:
 [CartesianIndices((1:3, 1:3, 2:2, 1:1)), CartesianIndices((1:3, 1:3, 2:2, 2:2))]
 [CartesianIndices((1:3, 1:3, 3:3, 1:1)), CartesianIndices((1:3, 1:3, 3:3, 2:2))]

julia> feature = rand(3, 2);

julia> feature_selector(feature)
 1-element Vector{Vector{CartesianIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}}}:
  [CartesianIndices((2:2, 1:1)), CartesianIndices((2:2, 2:2))]
```
