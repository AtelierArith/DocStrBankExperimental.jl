```
order(E::EllipticCurve{<: FinFieldElem}) -> ZZRingElem
```

有限体 $\mathbf F$ 上の楕円曲線 $E$ に対して、$\#E(\mathbf F)$ を計算します。

# 例

```jldoctest
julia> E = elliptic_curve(GF(101), [1, 2]);

julia> order(E)
100
```
