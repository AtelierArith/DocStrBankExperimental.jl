```
image(fs::Vector{Isogeny}, P::EllipticCurvePoint) -> EllipticCurvePoint
```

Return phi*n \circ phi*(n-1) \circ phi*1(P) where fs is a list of compatible isogenies [phi*1, ..., phi_n].
