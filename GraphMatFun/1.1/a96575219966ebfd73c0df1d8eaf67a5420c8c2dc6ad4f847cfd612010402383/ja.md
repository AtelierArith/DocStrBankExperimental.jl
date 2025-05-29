```
d = solve_linlsqr!(A, b, linlsqr, droptol)
```

線形最小二乗問題を解きます

```
Ad=b.
```

引数 `linlsqr` は線形最小二乗問題の解法を決定します。`:backslash`、 `:real_backslash`、 `:nrmeq`、 `:real_nrmeq`、 `:svd`、または `:real_svd` のいずれかを指定できます。後者の2つのオプションでは、 `droptol` 未満の特異値は無視されます。 `:real_X` オプションは、実ベクトルの空間で `d` を最適化します。入力行列 `A` は時々上書きされます。
