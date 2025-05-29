```
overapproximate(QM::QuadraticMap{N, <:SparsePolynomialZonotope},
                ::Type{<:SparsePolynomialZonotope}) where {N}
```

Overapproximate a quadratic map of a sparse polynomial zonotope with a sparse polynomial zonotope.

### Input

  * `QM`                       – quadratic map of a sparse polynomial zonotope
  * `SparsePolynomialZonotope` – target type

### Output

A sparse polynomial zonotope overapproximating the quadratic map of a sparse polynomial zonotope.

### Algorithm

This method implements [KochdumperA21; Proposition 13](@citet).
