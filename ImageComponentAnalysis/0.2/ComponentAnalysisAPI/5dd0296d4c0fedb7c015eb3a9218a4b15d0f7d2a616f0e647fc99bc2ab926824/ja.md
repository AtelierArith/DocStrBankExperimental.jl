```
analyze_components!(dataframe::AbstractDataFrame, components::AbstractArray{<:Integer}, f::AbstractComponentAnalysisAlgorithm, args...; kwargs...)
analyze_components!(dataframe::AbstractDataFrame, components::AbstractArray{<:Integer}, fs::Tuple{AbstractComponentAnalysisAlgorithm, Vararg{AbstractComponentAnalysisAlgorithm}}, args...; kwargs...)
```

接続されたコンポーネントをコンポーネント分析アルゴリズム `f` またはタプル `fs` で指定されたアルゴリズムのシーケンスを使用して分析し、結果を `DataFrame` に格納します。

# 出力

コンポーネントに関する情報は `DataFrame` に格納されます。各行番号は特定の接続コンポーネントに対応する情報を含みます。`DataFrame` はインプレースで変更され、列にはアルゴリズム `f` またはアルゴリズム `fs` が計算する測定値が格納されます。

# 例

アルゴリズムを `analyze_components!` に単純に渡すだけです：

```julia
df = DataFrame()
f = BasicMeasurement()
analyze_components!(df, components, f)

fs = tuple(RegionEllipse(), Contour())
analyze_components!(df, components, fs)
```

参照： [`analyze_components`](@ref)
