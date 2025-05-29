```
HyperellipticCurve(f::PolyRingElem, g::PolyRingElem; check::Bool = true) -> HypellCrv
```

Return the hyperelliptic curve $y^2 + h(x)y = f(x)$. The polynomial $f$ must be monic of degree 2g + 1 > 3 or of degree 2g + 2 > 4 and the polynomial h must be of degree < g + 2. Here g will be the genus of the curve.
