```
inner(
    ::Hyperbolic,
    p::PoincareHalfSpacePoint,
    X::PoincareHalfSpaceTangentVector,
    Y::PoincareHalfSpaceTangentVector
)
```

ポアンカレ半空間モデルにおける内積を計算します。式は次のようになります。

$$
g_p(X,Y) = \frac{⟨X,Y⟩}{p_n^2}.
$$
