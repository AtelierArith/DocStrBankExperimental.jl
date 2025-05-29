```
find_points((coefficients::Vector{ZZRingElem}, bound::IntegerUnion) -> ArbField
```

Given a list of coefficients [a*0, a*1, ..., a*n] and a bound, return a list of points (x, y) satisfying y^2 = a*0 + a*1*x + ... +a*n*x^n where writing x = a//b with gcd(a, b) = 1 the points are bounded by max(|a|, |b|) <= bound.
