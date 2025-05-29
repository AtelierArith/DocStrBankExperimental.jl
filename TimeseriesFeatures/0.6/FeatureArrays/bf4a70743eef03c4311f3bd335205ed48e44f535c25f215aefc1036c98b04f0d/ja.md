```
F = FeatureArray(data::AbstractArray, features::Union{Tuple{Symbol},Vector{Symbol}}, [timeseries::Union{Vector, Tuple}], args...)
```

`FeatureArray`を構築し、配列`data`に行に沿った`features`の名前を注釈し、オプションで列に沿った`timeseries`を注釈します。`FeatureArray <: AbstractFeatureArray <: AbstractDimArray`であるため、`FeatureArray`コンストラクタへのさらなる引数は`DimArray`コンストラクタに渡されます。特徴名にアクセスするには、`getnames(F)`を使用します。

# 例

```julia
data = rand(Int, 2, 10) # 2つの特徴と10の時系列を持つ特徴行列
F = FeatureArray(data, [:sum, :length])
```
