```
fullbases(n::Int; local_basis = "Pauli")
```

ローカルな単一量子ビット基底セットの選択に対して、測定基底の完全なセットを生成します。定義済みのオプション：

  * `local_basis = "Pauli"`: $3^n$ パウリ測定基底のセット
