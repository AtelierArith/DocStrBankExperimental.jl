```
normalizeBasis(b::GTBasisFuncs{T, D, 1}) where {T, D} -> GTBasisFuncs{T, D, 1}
```

Multiply the contraction coefficient(s) inside `b` by constant coefficient(s) to  normalizeBasis the `b`, and then return the normalized basis.
