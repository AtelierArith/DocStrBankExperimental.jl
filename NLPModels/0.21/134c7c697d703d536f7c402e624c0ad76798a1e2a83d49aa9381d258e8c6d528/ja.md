```
Jv = jprod_lin!(nlp, rows, cols, vals, v, Jv)
```

$$
J(x)v
$$

を評価します。ここで、ヤコビ行列は三重項形式で与えられています `(rows, cols, vals)`。
