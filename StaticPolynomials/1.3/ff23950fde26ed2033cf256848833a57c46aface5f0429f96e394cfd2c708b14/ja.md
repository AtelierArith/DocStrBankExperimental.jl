```
gradient!(u, f::Polynomial, x)
```

多項式 `f` の点 `x` における勾配を評価し、その結果を `u` に格納します。

```
gradient!(u, f::Polynomial, x, p)
```

パラメータ `p` を用いて点 `x` における多項式 `f` の勾配を評価し、その結果を `u` に格納します。
