```
FeatureArray{T, 1} where {T}
```

単一の時系列のための `FeatureArray` を構築するためのエイリアスです。

# 例

```julia
data = randn(2) # 1つの時系列のための特徴値
𝐟 = FeatureVector(data, [:sum, :length])
```
