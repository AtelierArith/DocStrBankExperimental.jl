```
Jtv = jtprod_residual!(nls, x, v, Jtv)
```

xにおける残差のヤコビ行列の転置とベクトルの積、すなわち、$J(x)^Tv$を計算し、それを`Jtv`に格納します。
