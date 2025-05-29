```
signature(f::ZZPolyRingElem)
```

$$
f
$$

のシグネチャを返します。すなわち、$r$が$f$の実根の数、$s$が複素根の数の半分であるタプル$(r, s)$を返します。

# 例

```jldoctest
julia> R, x = polynomial_ring(ZZ, "x");

julia> signature(x^3 + 3x + 1)
(1, 1)
```
