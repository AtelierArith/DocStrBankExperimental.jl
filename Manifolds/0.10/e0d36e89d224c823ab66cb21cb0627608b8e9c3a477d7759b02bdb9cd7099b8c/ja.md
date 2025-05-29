```
inner(::Hyperbolic, p::PoincareBallPoint, X::PoincareBallTangentVector, Y::PoincareBallTangentVector)
```

ポアンカレボールモデルにおける内積を計算します。式は次のようになります。

$$
g_p(X,Y) = \frac{4}{(1-\lVert p \rVert^2)^2}  ⟨X, Y⟩ .
$$
