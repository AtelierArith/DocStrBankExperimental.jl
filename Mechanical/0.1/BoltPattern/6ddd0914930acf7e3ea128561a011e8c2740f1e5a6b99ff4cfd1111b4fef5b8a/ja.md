```
bolt_centroid(points; A=1, return_all_data = false, udf_pivot = false)
```

ボルトパターンのボルト重心を計算します。

`points` は x および y 座標のタプル ([x], [y]) です。 `points` は関数 [`circle`](@ref) および [`rectangle`](@ref) によって生成される場合があります。 `A` はボルト応力面積で、すべてのボルトに対して単一の値として入力するか、各ボルトに対して異なる値（すなわちベクトル）を入力します。 `udf_pivot` は計算される場合は false で、特定のピボットポイントを手動で入力する場合は [x,y] として入力されます。 `Unitful` パッケージに準拠した単位が適用されるべきです。

# 例

```julia-repl
julia> using Unitful: mm
julia> bolt_centroid(([-100, 0, 100]mm, [100, 20, -60]mm))
(0.0 mm, 20.0 mm)
julia> bolt_centroid(([-100, 0, 100]mm, [100, 20, -60]mm), A=[3, 4, 5]mm^2)
(16.666666666666668 mm, 6.666666666666667 mm)
```
