```
division_polynomial(E::EllipticCurve, n::Int, x, y) -> Poly
```

Compute the n-th division polynomial of an elliptic curve defined over a field k following Mazur and Tate. When x and or y are given the output is automatically evaluated using the given values.
