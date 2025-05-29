```
coefficient(a::GenericAffExpr{C,V}, v1::V, v2::V) where {C,V}
```

Return the coefficient associated with the term `v1 * v2` in the quadratic expression `a`.

Note that `coefficient(a, v1, v2)` is the same as `coefficient(a, v2, v1)`.
