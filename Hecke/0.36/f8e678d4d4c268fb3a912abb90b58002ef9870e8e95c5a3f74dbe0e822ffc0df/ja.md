```
hasse_interval(E::EllipticCurve) -> (ZZRingElem, ZZRingElem)
```

有限体 $\mathbf F$ 上の楕円曲線 $E$ が与えられたとき、Hasseの定理を使用して、$l \leq \#E(\mathbf F) \leq b$ となる整数の配列 `[l, b]` を返します。

# 例

```jldoctest
julia> E = elliptic_curve(GF(3), [1, 2]);

julia> hasse_interval(E)
(0, 8)
```
