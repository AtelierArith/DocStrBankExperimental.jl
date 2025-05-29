```
hyperelliptic_polynomials([R::PolyRing,] E::EllipticCurve) -> PolyRingElem, PolyRingElem
```

$$
E
$$

が$y^2 + h*y = f$で与えられるような一変数多項式$f, h$を返します。

# 例

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2, 3, 4, 5]);

julia> hyperelliptic_polynomials(E)
(x^3 + 2*x^2 + 4*x + 5, x + 3)
```
