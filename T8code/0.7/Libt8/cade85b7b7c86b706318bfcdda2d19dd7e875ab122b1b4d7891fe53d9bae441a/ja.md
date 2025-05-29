```
t8_vec_axpy(vec_x, vec_y, alpha)
```

Y = Y + alpha * X

# 引数

  * `vec_x`:[in] 3Dベクトル。
  * `vec_y`:[in,out] 入力時は3Dベクトル。出力時は *vec_y* + *alpha* * *vec_x* に設定される。
  * `alpha`:[in] ファクター。

### プロトタイプ

```c
static inline void t8_vec_axpy (const double vec_x[3], double vec_y[3], const double alpha);
```
