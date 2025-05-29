```
q = project(M::SPDFixedDeterminant, p)
project!(M::SPDFixedDeterminant, q, p)
```

埋め込みから行列式 `M.d` の s.p.d. 行列の (部分) 多様体上に s.p.d. 行列 `p` を投影します（`q` の代わりに）。

式は次のようになります。

$$
q = \Bigl(\frac{d}{\det(p)}\Bigr)^{\frac{1}{n}}p
$$
