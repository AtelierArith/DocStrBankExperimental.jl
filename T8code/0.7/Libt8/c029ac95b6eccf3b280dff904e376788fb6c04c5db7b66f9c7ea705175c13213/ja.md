```
t8_geom_get_ref_intersection(edge_index, ref_coords, ref_intersection)
```

三角形の参照空間における交点を計算します。交点は、参照点と辺の反対の頂点を通る直線の延長です。 /|\ / | \ o -> 参照点 / o \ x -> 交点 / | \ /____x____

# 引数

  * `edge_index`:[in] 交点が存在する辺のインデックス。
  * `ref_coords`:[in] 参照点の座標を含む配列。
  * `ref_intersection`:[out] 交点の座標。

### プロトタイプ

```c
void t8_geom_get_ref_intersection (int edge_index, const double *ref_coords, double ref_intersection[2]);
```
