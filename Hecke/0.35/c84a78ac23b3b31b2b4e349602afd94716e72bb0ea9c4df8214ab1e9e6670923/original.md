```
stable_faltings_height(E::EllipticCurve{QQFieldElem}, prec::Int) -> Float64
```

Return the stable Faltings height of E. This is defined as 1/12*(log(denominator(j)) - abs(delta))-1/2log(A) where j is the j-invariant, delta is the discriminant and A is the covolume of the period lattice of the chosen model of E.
