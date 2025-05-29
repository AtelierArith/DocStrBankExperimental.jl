```
find_points(E::EllipticCurve{QQFieldElem}, bound::IntegerUnion) -> ArbField
```

与えられた整数係数のQQ上の楕円曲線Eと境界に対して、x = a//bと書くことができ、gcd(a, b) = 1である点のリスト（x: y: 1）を曲線上に返します。これらの点はmax(|a|, |b|) <= boundによって制約されています。
