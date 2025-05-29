```
t8_cmesh_translate_coordinates(coords_in, coords_out, num_vertices, translate)
```

配列のダブルに対して y = x + translate を計算し、各3を1つのベクトルxとして解釈します。

# 引数

  * `coords_in`:[in] ベクトルの入力座標
  * `coords_out`:[out] 計算されたベクトルの座標
  * `num_vertices`:[in] 頂点/ベクトルの数
  * `translate`:[in] ベクトルの平行移動。

### プロトタイプ

```c
void t8_cmesh_translate_coordinates (const double *coords_in, double *coords_out, const int num_vertices, const double translate[3]);
```
