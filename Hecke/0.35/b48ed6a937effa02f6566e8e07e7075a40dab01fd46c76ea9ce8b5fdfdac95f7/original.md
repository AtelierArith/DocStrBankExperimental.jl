```
tates_algorithm_local(E::EllipticCurve{AbsSimpleNumFieldElem}, p:: AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem})
-> EllipticCurve{AbsSimpleNumFieldElem}, String, ZZRingElem, ZZRingElem, Bool
```

Returns a tuple $(\tilde E, K, m, f, c, s)$, where $\tilde E$ is a minimal model for $E$ at the prime ideal $p$, $K$ is the Kodaira symbol, $f$ is the conductor valuation at $p$, $c$ is the local Tamagawa number at $p$ and `s` is false if and only if $E$ has non-split multiplicative reduction.
