```
tate_pairing(P::EllipticCurvePoint{T}, Q::EllipticCurvePoint{T}, n::Int) where T
```

有限体 $K$ 上の楕円曲線上の $n$-トーション点 $P$ と別の点 $Q$ が与えられたとき、$n$-次の冪の剰余類の代表を返すことによって Tate ペアリング $t_n(P, Q)$ を返します。

$$
n
$$

-次の根が必要な場合は、[reduced*tate*pairing](@ref) を参照してください。
