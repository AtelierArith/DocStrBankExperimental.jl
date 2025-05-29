```
t8_vertex_point_inside(vertex_coords, point, tolerance)
```

頂点内に点があるかどうかを確認します

# 引数

  * `vertex_coords`:[in] 頂点の座標
  * `point`:[in] 確認する点の座標
  * `tolerance`:[in] 許容範囲を定義する 0 より大きい倍精度浮動小数点数

# 戻り値

点が外側にある場合は 0、そうでない場合は 1。

### プロトタイプ

```c
int t8_vertex_point_inside (const double vertex_coords[3], const double point[3], const double tolerance);
```
