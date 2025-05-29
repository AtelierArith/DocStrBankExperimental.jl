```
project(M::KendallsPreShapeSpace, p)
```

Project point `p` from the embedding to [`KendallsPreShapeSpace`](@ref) by selecting the right element from the orthogonal section representing the quotient manifold `M`. See Section 3.7 of [SrivastavaKlassen:2016](@cite) for details.

The method computes the mean of the landmarks and moves them to make their mean zero; afterwards the Frobenius norm of the landmarks (as a matrix) is normalised to fix the scaling.
