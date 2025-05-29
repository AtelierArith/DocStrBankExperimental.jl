```
t8_mat_mult_vec(mat, a, b)
```

行列-ベクトルの乗算を適用します: b = M*a。

# 引数

  * `mat`:[in] 3x3行列。
  * `a`:[in] 3次元ベクトル。
  * `b`:[in,out] 3次元ベクトル。

### プロトタイプ

```c
static inline void t8_mat_mult_vec (const double mat[3][3], const double a[3], double b[3]);
```
