```
t8_cmesh_coords_axb(coords_in, coords_out, num_vertices, alpha, b)
```

配列のダブルに対して y = ax + b を計算し、各3を1つのベクトル x として解釈します。

# 引数

  * `coords_in`:[in] ベクトルの入力座標
  * `coords_out`:[out] 計算されたベクトルの座標
  * `num_vertices`:[in] 頂点/ベクトルの数
  * `alpha`:[in] ベクトルのスケーリング係数
  * `b`:[in] ベクトルの平行移動。

### プロトタイプ

```c
void t8_cmesh_coords_axb (const double *coords_in, double *coords_out, int num_vertices, double alpha, const double b[3]);
```
