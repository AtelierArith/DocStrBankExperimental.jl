```
is_probable_supersingular(E::EllipticCurve{T}) where T <: FinFieldElem
```

Uses a probabilistic algorithm to test whether E is supersingular or not. If the function returns false, the curve is proven to be ordinary. If the function returns true, there is a high chance the curve is supersingular, but the result hasn't been proven.
