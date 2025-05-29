```
analyze_components(components::AbstractArray{<:Integer}, f::AbstractComponentAnalysisAlgorithm, args...; kwargs...)
analyze_components(components::AbstractArray{<:Integer}, f::Tuple{AbstractComponentAnalysisAlgorithm, Vararg{AbstractComponentAnalysisAlgorithm}}, args...; kwargs...)
```

アルゴリズム `f` またはタプル `fs` で指定されたアルゴリズムのシーケンスを使用して接続されたコンポーネントを分析し、結果を `DataFrame` に格納します。

# 出力

コンポーネントに関する情報は `DataFrame` に格納されます。各行番号は特定の接続コンポーネントに対応する情報を含みます。`DataFrame` の列には、アルゴリズム `f` またはアルゴリズム `fs` が計算する測定値が格納されます。

# 例

ラベル付き接続コンポーネントの配列とコンポーネント分析アルゴリズムを `analyze_component` に渡します。

```julia
f = BasicMeasurement()
analyze_components = analyze_component(components, f)

fs = tuple(RegionEllipse(), Contour())
analyze_components!(df, components, fs)
```

最初の例は「アルゴリズム `f` を使用して接続された `components` の `analyze_components`」と読み取れます。

既存の `DataFrame` に接続コンポーネントに関する情報を追加するための [`analyze_components!`](@ref) も参照してください。 ```
