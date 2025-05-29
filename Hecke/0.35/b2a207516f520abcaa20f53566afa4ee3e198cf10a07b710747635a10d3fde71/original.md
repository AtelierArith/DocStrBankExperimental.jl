```
pr_torsion_basis(E::EllipticCurve{AbsSimpleNumFieldElem}, p::ZZRingElem, r = Int) -> Vector{EllipticCurvePoint}
```

Compute a basis for the p-power torsion subgroup. When r is given the algorithm stops searching after having found a basis that spans p^r points.
