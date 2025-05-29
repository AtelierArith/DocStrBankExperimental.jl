```
t8_vec_axy(vec_x, vec_y, alpha)
```

Y = α * X を計算します。

# 引数

  * `vec_x`:[in] 3Dベクトル。
  * `vec_z`:[out] 出力時に *α* * *vec_x* に設定されます。
  * `alpha`:[in] ファクター。

### プロトタイプ

```c
static inline void t8_vec_axy (const double vec_x[3], double vec_y[3], const double alpha);
```
