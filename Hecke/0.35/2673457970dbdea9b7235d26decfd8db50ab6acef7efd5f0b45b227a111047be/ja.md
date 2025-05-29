```
CPS_height_bounds(E::EllipticCurve) -> ArbFieldElem, ArbFieldElem
```

数体または有理体上の楕円曲線が与えられたとき、楕円曲線 E のナイーブ高さと標準高さの差の境界を与えるタプル `a, b` を返します。すべての E の有理点 `P` に対して、`a <= naive_height(P) - canonical_height(P) <= b` となります。
