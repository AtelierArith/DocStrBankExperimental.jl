```
t8_vec_ax(vec_x, alpha)
```

X = alpha * Xを計算します。

# 引数

  * `vec_x`:[in,out] 3Dベクトル。出力時に*alpha* * *vec_x*に設定されます。
  * `alpha`:[in] ファクター。

### プロトタイプ

```c
static inline void t8_vec_ax (double vec_x[3], const double alpha);
```
