```
t8_vec_dist(vec_x, vec_y)
```

XとYのユークリッド距離。

# 引数

  * `vec_x`:[in] 3Dベクトル。
  * `vec_y`:[in] 3Dベクトル。

# 戻り値

ユークリッド距離。norm (X-Y) と同等。

### プロトタイプ

```c
static inline double t8_vec_dist (const double vec_x[3], const double vec_y[3]);
```
