```
t8_mat_init_zrot(mat, angle)
```

与えられた角度でz軸周りの回転行列として3x3行列を初期化します。

# 引数

  * `mat`:[in,out] 3x3行列。
  * `angle`:[in] ラジアンでの回転角。

### プロトタイプ

```c
static inline void t8_mat_init_zrot (double mat[3][3], const double angle);
```
