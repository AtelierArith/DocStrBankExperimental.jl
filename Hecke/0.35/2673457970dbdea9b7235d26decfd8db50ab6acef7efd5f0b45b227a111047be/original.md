```
CPS_height_bounds(E::EllipticCurve) -> ArbFieldElem, ArbFieldElem
```

Given an elliptic curve over a number field or rational field, return a tuple `a, b` giving bounds for the difference between the naive and the canonical height of an elliptic curve E. We have `a <= naive_height(P) - canonical_height(P) <= b` for all rational points `P` of `E`.
