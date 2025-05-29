```
voronoiplot(x, y, values; kwargs...)
voronoiplot(values; kwargs...)
voronoiplot(x, y; kwargs...)
voronoiplot(positions; kwargs...)
voronoiplot(vorn::VoronoiTessellation; kwargs...)
```

`heatmap`または点状データからVoronoiタイルを生成してプロットします。タイルはDelaunayTriangulation.jlからの`VoronoiTessellation`として直接渡すこともできます。

## 属性

  * `show_generators = true`は、個々の生成器をプロットするかどうかを決定します。
  * `markersize = 12`は、ポイントのサイズを設定します。
  * `marker = :circle`は、ポイントの形状を設定します。
  * `markercolor = :black`は、ポイントの色を設定します。
  * `strokecolor = :black`は、多角形のストロークカラーを設定します。
  * `strokewidth = 1`は、多角形のストロークの幅を設定します。
  * `color = automatic`は、多角形の色を設定します。`automatic`の場合、多角形はカラーマップに従って個別に色付けされます。
  * `unbounded_edge_extension_factor = 0.1`は、`DelaunayTriangulation.polygon_bounds`で使用される無限辺の拡張係数を設定します。
  * `clip::Union{Automatic, Rect2, Circle, Tuple} = automatic`は、生成された多角形のクリッピングエリアを設定します。これは`Rect2`（または`BBox`）、エントリ`(xmin, xmax, ymin, ymax)`を持つ`Tuple`、または`Circle`として指定できます。指定されたエリアの外側は削除されます。`clip`が設定されていない場合は、`unbounded_edge_extension_factor`を使用して自動的に決定されます。

### 色の属性

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis`は、数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()`を呼び出すことができます。
  * `colorscale::Function = identity`は、色変換関数です。任意の関数を使用できますが、`Colorbar`と一緒に`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`、および`Makie.Symlog10`と一緒にうまく機能します。
  * `colorrange::Tuple{<:Real, <:Real}`は、`colormap`の開始点と終了点を表す値を設定します。
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)`は、`color = NaN`の置き換え色を設定します。
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing`は、カラーレンジ未満の任意の値の色を設定します。
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing`は、カラーレンジを超える任意の値の色を設定します。
  * `alpha = 1.0`は、カラーマップまたは色属性のアルファ値を設定します。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファがある場合、掛け算されます。
