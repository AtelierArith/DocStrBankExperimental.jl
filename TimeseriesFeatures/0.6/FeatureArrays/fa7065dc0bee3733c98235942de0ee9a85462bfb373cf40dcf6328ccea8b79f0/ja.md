```
FeatureArray{T, 2} where {T}
```

フラットな時系列のセットのための `FeatureArray` を構築するエイリアスです。

# 例

```julia
data = rand(Int, 2, 3) # 2つの特徴と3つの時系列を持つ特徴行列
F = FeatureMatrix(data, [:sum, :length], [1, 2, 3])
```
