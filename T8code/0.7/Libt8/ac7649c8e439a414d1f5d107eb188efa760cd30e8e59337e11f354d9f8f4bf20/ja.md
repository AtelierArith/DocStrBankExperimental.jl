```
t8_vec_cross(vec_x, vec_y, cross)
```

XとYの外積

# 引数

  * `vec_x`:[in] 3Dベクトル。
  * `vec_y`:[in] 3Dベクトル。
  * `cross`:[out] 出力として、*vec_x*と*vec_y*の外積。

### プロトタイプ

```c
static inline void t8_vec_cross (const double vec_x[3], const double vec_y[3], double cross[3]);
```
