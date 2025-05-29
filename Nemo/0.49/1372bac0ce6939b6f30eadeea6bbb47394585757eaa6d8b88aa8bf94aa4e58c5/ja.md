```
signature(f::QQPolyRingElem)
```

$$
f
$$

のシグネチャ、すなわち、$f$の実根の数$r$と複素根の数の半分$s$からなるタプル$(r, s)$を返します。

# 例

```jldoctest
julia> R, x = polynomial_ring(QQ, "x");

julia> signature(x^3 + 3x + 1)
(1, 1)
```
