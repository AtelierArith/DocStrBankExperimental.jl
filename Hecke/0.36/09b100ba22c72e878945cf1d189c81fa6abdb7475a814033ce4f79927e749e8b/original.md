```
rescale(T::TorQuadModule, k::RingElement) -> TorQuadModule
```

Return the torsion quadratic module with quadratic form scaled by $k$, where k is a non-zero rational number. If the old form was defined modulo `n`, then the new form is defined modulo `n k`.
