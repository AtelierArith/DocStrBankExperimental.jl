```
coefficients(E::EllipticCurve{T}) -> Tuple{T, T, T, T, T}
```

Return the Weierstrass coefficients of $E$ as a tuple (a1, a2, a3, a4, a6) such that $E$ is given by y^2 + a1xy + a3y = x^3 + a2x^2 + a4x + a6.
