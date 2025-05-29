```
find_points((coefficients::Vector{ZZRingElem}, bound::IntegerUnion) -> ArbField
```

与えられた係数のリスト [a*0, a*1, ..., a*n] と境界に対して、y^2 = a*0 + a*1*x + ... + a*n*x^n を満たす点 (x, y) のリストを返します。ここで、x = a//b と書くとき、gcd(a, b) = 1 であり、点は max(|a|, |b|) <= bound によって制約されます。
