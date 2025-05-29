```
t8_vec_diff(vec_x, vec_y, diff)
```

2つのベクトルの差を計算します。

# 引数

  * `vec_x`:[in] 3Dベクトル。
  * `vec_y`:[in] 3Dベクトル。
  * `diff`:[out] 出力として、*vec_x* と *vec_y* の差。

### プロトタイプ

```c
static inline void t8_vec_diff (const double vec_x[3], const double vec_y[3], double diff[3]);
```
