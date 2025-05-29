```
Polynomial{T}
```

多項式近似型を表します（有限差分とは対照的です）。デフォルトでは、`Polynomial()`は`Polynomial{StartUpDG.DefaultPolynomialType}`を構築します。型パラメータを指定することで、多項式近似内の追加構造に基づいてディスパッチを行うことができます（例：コレクション、テンソル積数値積分など）。
