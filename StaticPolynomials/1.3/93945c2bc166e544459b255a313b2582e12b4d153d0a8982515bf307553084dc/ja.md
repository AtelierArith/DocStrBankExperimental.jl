```
evaluate_and_gradient!(u, f::Polynomial, x)
```

多項式 `f` とその勾配を `x` で評価します。勾配を `u` に格納し、`f(x)` を返します。

```
evaluate_and_gradient!(u, f::Polynomial, x, p)
```

パラメータ `p` を用いて `x` で多項式 `f` とその勾配を評価します。勾配を `u` に格納し、`f(x)` を返します。
