```
triplot(x, y; kwargs...)
triplot(positions; kwargs...)
triplot(triangles::Triangulation; kwargs...)
```

与えられた位置または DelaunayTriangulation.jl からの `Triangulation` に基づいて三角形分割をプロットします。

## プロットタイプ

`triplot` 関数のプロットタイプエイリアスは `Triplot` です。

## 属性

**`bounding_box`** =  `automatic`  — ゴーストエッジを切り取るためのバウンディングボックスを設定します。これは `Rect2`（または `BBox`）または `(xmin, xmax, ymin, ymax)` の形式のタプルであることができます。デフォルトでは、長方形は `[a - eΔx, b + eΔx] × [c - eΔy, d + eΔy]` で与えられ、ここで `e` は `ghost_edge_extension_factor`、`Δx = b - a` および `Δy = d - c` は長方形の辺の長さであり、`[a, b] × [c, d]` は三角形分割内の点のバウンディングボックスです。

**`constrained_edge_color`** =  `:magenta`  — 制約されたエッジの色を設定します。

**`constrained_edge_linestyle`** =  `@inherit linestyle`  — 制約されたエッジの線スタイルを設定します。

**`constrained_edge_linewidth`** =  `@inherit linewidth`  — 制約されたエッジの幅を設定します。

**`convex_hull_color`** =  `:red`  — 凸包の色を設定します。

**`convex_hull_linestyle`** =  `:dash`  — 凸包の線スタイルを設定します。

**`convex_hull_linewidth`** =  `@inherit linewidth`  — 凸包の幅を設定します。

**`ghost_edge_color`** =  `:blue`  — ゴーストエッジの色を設定します。

**`ghost_edge_extension_factor`** =  `0.1`  — 外部ゴーストエッジが拡張される長方形の拡張係数を設定します。

**`ghost_edge_linestyle`** =  `@inherit linestyle`  — ゴーストエッジの線スタイルを設定します。

**`ghost_edge_linewidth`** =  `@inherit linewidth`  — ゴーストエッジの幅を設定します。

**`joinstyle`** =  `@inherit joinstyle`  — *ドキュメントは利用できません。*

**`linecap`** =  `@inherit linecap`  — *ドキュメントは利用できません。*

**`linestyle`** =  `:solid`  — 三角形のエッジの線スタイルを設定します。

**`marker`** =  `@inherit marker`  — 点の形状を設定します。

**`markercolor`** =  `@inherit markercolor`  — 点の色を設定します。

**`markersize`** =  `@inherit markersize`  — 点のサイズを設定します。

**`miter_limit`** =  `@inherit miter_limit`  — *ドキュメントは利用できません。*

**`recompute_centers`** =  `false`  — ゴーストエッジの向きの代表点を再計算するかどうかを決定します。これは `tri.representative_point_list` を直接変更しますので注意してください。

**`show_constrained_edges`** =  `false`  — 制約されたエッジをプロットするかどうかを決定します。

**`show_convex_hull`** =  `false`  — 凸包をプロットするかどうかを決定します。

**`show_ghost_edges`** =  `false`  — ゴーストエッジをプロットするかどうかを決定します。

**`show_points`** =  `false`  — 個々の点をプロットするかどうかを決定します。これは三角形分割に含まれる点のみをプロットしますので注意してください。

**`strokecolor`** =  `@inherit patchstrokecolor`  — 三角形のエッジの色を設定します。

**`strokewidth`** =  `1`  — 三角形のエッジの線幅を設定します。

**`triangle_color`** =  `:transparent`  — 三角形の色を設定します。
