```
t8_geom_get_scaling_factor_of_edge_on_face_tet(edge_index, face_index, ref_coords)
```

テトラヘドラル要素の面上のエッジの変位のスケーリングファクターを計算します。

# 引数

  * `edge_index`:[in] 変位をスケーリングするエッジのインデックス。
  * `face_index`:[in] 変位をスケーリングする面のインデックス。
  * `ref_coords`:[in] 参照点の座標を含む配列。

# 戻り値

参照座標の点での面上のエッジ変位のスケーリングファクター。

### プロトタイプ

```c
double t8_geom_get_scaling_factor_of_edge_on_face_tet (int edge_index, int face_index, const double *ref_coords);
```
