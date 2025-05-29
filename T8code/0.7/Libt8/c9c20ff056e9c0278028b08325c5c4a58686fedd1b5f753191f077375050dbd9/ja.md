```
t8_vec_axb(vec_x, vec_y, alpha, b)
```

Y = α * X + b

!!! note
    入力時に vec*x = vec*y である可能性があり、x を上書きします


# 引数

  * `vec_x`:[in] 3D ベクトル。
  * `vec_y`:[out] 入力時、3D ベクトル。出力時に *alpha* * *vec_x* + *b* に設定されます。
  * `alpha`:[in] ファクター。
  * `b`:[in] オフセット。

### プロトタイプ

```c
static inline void t8_vec_axb (const double vec_x[3], double vec_y[3], const double alpha, const double b);
```
