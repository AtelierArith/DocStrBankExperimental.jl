```
vals = jth_hess_coord!(nlp, x, j, vals)
```

`x`におけるj番目の制約のヘッセ行列をスパース座標形式で評価し、長さ`nlp.meta.nnzh`の`vals`に格納します。下三角のみが返されます。
