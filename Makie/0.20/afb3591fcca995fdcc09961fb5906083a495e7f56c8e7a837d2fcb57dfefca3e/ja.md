```
triplot(x, y; kwargs...)
triplot(positions; kwargs...)
triplot(triangles::Triangulation; kwargs...)
```

提供された位置または DelaunayTriangulation.jl からの `Triangulation` に基づいて三角形分割をプロットします。

## 属性

  * `show_points = false` は、個々の点をプロットするかどうかを決定します。これは、三角形分割に含まれる点のみをプロットします。
  * `show_convex_hull = false` は、凸包をプロットするかどうかを決定します。
  * `show_ghost_edges = false` は、ゴーストエッジをプロットするかどうかを決定します。
  * `show_constrained_edges = false` は、制約エッジをプロットするかどうかを決定します。
  * `recompute_centers = false` は、ゴーストエッジの向きの代表点を再計算するかどうかを決定します。これは `tri.representative_point_list` を直接変更します。
  * `markersize = 12` は、点のサイズを設定します。
  * `marker = :circle` は、点の形状を設定します。
  * `markercolor = :black` は、点の色を設定します。
  * `strokecolor = :black` は、三角形のエッジの色を設定します。
  * `strokewidth = 1` は、三角形のエッジの線幅を設定します。
  * `linestyle = :solid` は、三角形のエッジの線スタイルを設定します。
  * `triangle_color = (:white, 0.0)` は、三角形の色を設定します。
  * `convex_hull_color = :red` は、凸包の色を設定します。
  * `convex_hull_linestyle = :dash` は、凸包の線スタイルを設定します。
  * `convex_hull_linewidth = 1` は、凸包の幅を設定します。
  * `ghost_edge_color = :blue` は、ゴーストエッジの色を設定します。
  * `ghost_edge_linestyle = :solid` は、ゴーストエッジの線スタイルを設定します。
  * `ghost_edge_linewidth = 1` は、ゴーストエッジの幅を設定します。
  * `ghost_edge_extension_factor = 0.1` は、外部ゴーストエッジが拡張される矩形の拡張係数を設定します。
  * `bounding_box::Union{Automatic, Rect2, Tuple} = automatic`: ゴーストエッジを切り取るためのバウンディングボックスを設定します。これは `Rect2`（または `BBox`）または形式 `(xmin, xmax, ymin, ymax)` のタプルであることができます。デフォルトでは、矩形は `[a - eΔx, b + eΔx] × [c - eΔy, d + eΔy]` で与えられ、ここで `e` は `ghost_edge_extension_factor`、`Δx = b - a` および `Δy = d - c` は矩形の辺の長さであり、`[a, b] × [c, d]` は三角形分割内の点のバウンディングボックスです。
  * `constrained_edge_color = :magenta` は、制約エッジの色を設定します。
  * `constrained_edge_linestyle = :solid` は、制約エッジの線スタイルを設定します。
  * `constrained_edge_linewidth = 1` は、制約エッジの幅を設定します。
