```
t8_geom_get_scaling_factor_of_edge_on_face_prism(edge_index, face_index, ref_coords)
```

プリズム要素の面上のエッジの変位のスケーリングファクターを計算します。

# 引数

  * `edge_index`:[in] スケーリングされるべきエッジのインデックス。
  * `face_index`:[in] 変位がスケーリングされるべき面のインデックス。
  * `ref_coords`:[in] 参照点の座標を含む配列。

# 戻り値

参照座標の点での面上のエッジ変位のスケーリングファクター。

### プロトタイプ

```c
double t8_geom_get_scaling_factor_of_edge_on_face_prism (int edge_index, int face_index, const double *ref_coords);
```
