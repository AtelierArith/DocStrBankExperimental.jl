```
Jtv = jtprod_lin!(nlp, rows, cols, vals, v, Jtv)
```

$$
J(x)^Tv
$$

を評価します。ここで、ヤコビアンは三重項形式で`(rows, cols, vals)`によって与えられます。
