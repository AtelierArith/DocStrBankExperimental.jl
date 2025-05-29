```
order(P::EllipticCurvePoint, [fac::Fac{ZZRingElem}]) -> ZZRingElem
```

有限体上の楕円曲線 $E$ の点 $P$ に対して、この点の位数を返します。

オプションとして、点の位数の倍数の因数分解を提供することができます。例えば、$E$ の位数の因数分解です。

# 例

```jldoctest
julia> E = elliptic_curve(GF(101), [1, 2]);

julia> P = E([17, 65]);

julia> order(P)
100

julia> fac = factor(order(E))
1 * 5^2 * 2^2

julia> order(P, fac)
100
```
