```
vals = jac_lin_coord!(nlp, x, vals)
```

$$
J(x)
$$

を評価し、スパース座標形式で`x`における線形制約のヤコビアンを`vals`に上書きします。
