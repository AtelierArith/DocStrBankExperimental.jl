```
preserves_angles(f::Transformation)
```

Return `true` if `f``is angle-preserving (has equal-magnitude eigenvalues) and`false` otherwise.

Uses approximate equality to allow for floating point imprecision.
