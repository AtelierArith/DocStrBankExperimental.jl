```
elliptic_curve(f::MPolyRingElem, x::MPolyRingElem, y::MPolyRingElem) -> EllipticCurve
```

Construct an elliptic curve from a bivariate polynomial `f` in long Weierstrass form. The second and third argument specify variables of the `parent` of `f` so that $f = c ⋅ (-y² + x³ - a₁ ⋅ xy + a₂ ⋅ x² - a₃ ⋅ y + a₄ ⋅ x + a₆)$.
