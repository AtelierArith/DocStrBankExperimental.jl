```
Jtv = jtprod_residual!(nls, rows, cols, vals, v, Jtv)
```

与えられた `(rows, cols, vals)` による残差のヤコビ行列の転置の積をベクトルと計算します。すなわち、$J(x)^Tv$ を計算し、`Jv` に格納します。
