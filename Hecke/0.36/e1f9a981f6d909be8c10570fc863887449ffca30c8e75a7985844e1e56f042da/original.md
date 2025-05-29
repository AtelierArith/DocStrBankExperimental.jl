```
find_points(E::EllipticCurve{QQFieldElem}, bound::IntegerUnion) -> ArbField
```

Given an elliptic curve E over QQ with integral coefficients and a bound, return a list of points (x: y: 1) on the curve where writing x = a//b with gcd(a, b) = 1 the points are bounded by max(|a|, |b|) <= bound.
