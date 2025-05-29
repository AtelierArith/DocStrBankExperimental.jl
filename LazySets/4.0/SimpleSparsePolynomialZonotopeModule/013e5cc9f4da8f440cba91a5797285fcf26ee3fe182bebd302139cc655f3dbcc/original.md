```
quadratic_map(Q::Vector{<:AbstractMatrix}, S::SimpleSparsePolynomialZonotope)
```

Return the quadratic map of a simple sparse polynomial zonotope.

### Input

  * `Q` – vector of square matrices
  * `S` – simple sparse polynomial zonotope

### Output

The quadratic map of `P` represented as a simple sparse polynomial zonotope.

### Algorithm

This method implements [KochdumperA21; Proposition 12](@citet). See also [Kochdumper21a; Proposition 3.1.30](@citet).
