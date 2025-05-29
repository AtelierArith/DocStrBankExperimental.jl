```
t8_mat_mult_mat(A, B, C)
```

行列の行列積を適用します: C = A*B。

# 引数

  * `A`:[in] 3x3行列。
  * `B`:[in] 3x3行列。
  * `C`:[in] 3x3行列。

### プロトタイプ

```c
static inline void t8_mat_mult_mat (const double A[3][3], const double B[3][3], double C[3][3]);
```
