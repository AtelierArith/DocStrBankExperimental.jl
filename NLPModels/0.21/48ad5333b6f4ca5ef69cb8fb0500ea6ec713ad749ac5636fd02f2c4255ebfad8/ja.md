```
vals = jac_coord_residual!(nls, x, vals)
```

`x`における残差のヤコビアンをスパース座標形式で計算し、`vals`を書き換えます。`rows`と`cols`は書き換えられません。
