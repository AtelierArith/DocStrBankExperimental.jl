```
vals = hess_coord_residual!(nls, x, v, vals)
```

`x`における残差のヘッセ行列の線形結合を、係数`v`を用いてスパース座標形式で計算し、`vals`を書き換えます。
