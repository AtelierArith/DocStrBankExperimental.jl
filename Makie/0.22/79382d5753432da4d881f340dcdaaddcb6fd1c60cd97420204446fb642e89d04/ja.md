```
voronoiplot(x, y, values; kwargs...)
voronoiplot(values; kwargs...)
voronoiplot(x, y; kwargs...)
voronoiplot(positions; kwargs...)
voronoiplot(vorn::VoronoiTessellation; kwargs...)
```

`heatmap`または点状データからVoronoiタイルを生成してプロットします。タイルはDelaunayTriangulation.jlからの`VoronoiTessellation`として直接渡すこともできます。

## プロットタイプ

`voronoiplot`関数のプロットタイプエイリアスは`Voronoiplot`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)`のように複数のアルファは掛け算されます。

**`clip`** =  `automatic`  — 生成されたポリゴンのクリッピングエリアを設定します。これは`Rect2`（または`BBox`）、エントリ`(xmin, xmax, ymin, ymax)`を持つ`Tuple`、または`Circle`として指定できます。指定されたエリアの外側は削除されます。`clip`が設定されていない場合は、`unbounded_edge_extension_factor`を使用して自動的に決定されます。

**`color`** =  `automatic`  — ポリゴンの色を設定します。`automatic`の場合、ポリゴンはカラーマップに従って個別に色付けされます。

**`colormap`** =  `@inherit colormap :viridis`  — 数値`color`のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)`も使用できますし、ColorBrewerやPlotUtilsの任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを見るには、`Makie.available_gradients()`を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap`の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10`、および`Makie.Symlog10`と一緒に使用する場合にのみうまく機能します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`marker`** =  `@inherit marker`  — ポイントの形状を設定します。

**`markercolor`** =  `@inherit markercolor`  — ポイントの色を設定します。

**`markersize`** =  `@inherit markersize`  — ポイントのサイズを設定します。

**`nan_color`** =  `:transparent`  — NaN値の色。

**`show_generators`** =  `true`  — 個々のジェネレーターをプロットするかどうかを決定します。

**`smooth`** =  `false`  — *ドキュメントは利用できません。*

**`strokecolor`** =  `@inherit patchstrokecolor`  — ポリゴンのストロークカラーを設定します。

**`strokewidth`** =  `1.0`  — ポリゴンのストロークの幅を設定します。

**`unbounded_edge_extension_factor`** =  `0.1`  — `DelaunayTriangulation.polygon_bounds`で使用される無限境界のエッジの拡張係数を設定します。
