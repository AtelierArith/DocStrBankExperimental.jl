```
t8_vec_axpyz(vec_x, vec_y, vec_z, alpha)
```

Z = Y + alpha * X

# 引数

  * `vec_x`:[in] 3Dベクトル。
  * `vec_y`:[in] 3Dベクトル。
  * `vec_z`:[out] 出力時に *vec_y* + *alpha* * *vec_x* に設定されます。

### プロトタイプ

```c
static inline void t8_vec_axpyz (const double vec_x[3], const double vec_y[3], double vec_z[3], const double alpha);
```
