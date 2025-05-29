```
t8_geom_get_triangle_scaling_factor(edge_index, tree_vertices, glob_intersection, glob_ref_point)
```

三角形のツリーフェイスに沿ったエッジの変位のスケーリングファクターを、グローバル参照点の位置に応じて計算します。

# 引数

  * `edge_index`:[in] 変位をスケーリングするエッジのインデックス。
  * `tree_vertices`:[in] ツリーの頂点座標を含む配列。
  * `glob_intersection`:[in] エッジインデックスに対して、グローバル参照点を通る反対の頂点から引かれた線の交点の座標を含む配列。
  * `glob_ref_point`:[in] グローバル空間にマッピングされた参照点の座標を含む配列。

### プロトタイプ

```c
double t8_geom_get_triangle_scaling_factor (int edge_index, const double *tree_vertices, const double *glob_intersection, const double *glob_ref_point);
```
