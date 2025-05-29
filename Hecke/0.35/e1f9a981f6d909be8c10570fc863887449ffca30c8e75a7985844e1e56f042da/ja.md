```
find_points(E::EllipticCurve{QQFieldElem}, bound::IntegerUnion) -> ArbField
```

与えられた有理数係数の楕円曲線 E と境界に対して、x = a//b と書ける点 (x: y: 1) のリストを返します。ただし、gcd(a, b) = 1 であり、点は max(|a|, |b|) <= bound によって制限されます。
