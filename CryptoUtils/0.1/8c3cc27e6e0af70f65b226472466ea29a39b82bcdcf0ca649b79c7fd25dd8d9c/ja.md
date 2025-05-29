```
factor_with_ed(n::Integer, e::Integer, d::Integer) -> (Integer, Integer)
```

`n = p*q` を因数分解します。ここで `(e, d)` は `e*d = 1 mod phi(n)` となります。Stinson ページ 204 - アルゴリズム 5.10
