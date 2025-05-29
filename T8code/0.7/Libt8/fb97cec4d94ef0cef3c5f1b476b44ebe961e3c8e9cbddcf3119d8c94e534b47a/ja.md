```
t8_vec_eq(vec_x, vec_y, tol)
```

2つのベクトルの要素ごとの等価性をチェックします

# 引数

  * `vec_x`:[in]
  * `vec_y`:[in]
  * `tol`:[in]

# 戻り値

ベクトルが *tol* まで等しい場合は true

### プロトタイプ

```c
static inline int t8_vec_eq (const double vec_x[3], const double vec_y[3], const double tol);
```
