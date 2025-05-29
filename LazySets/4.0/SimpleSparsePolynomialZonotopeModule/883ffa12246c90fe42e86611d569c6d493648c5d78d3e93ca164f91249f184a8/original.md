```
quadratic_map(Q::Vector{<:AbstractMatrix}, S1::SimpleSparsePolynomialZonotope,
              S2::SimpleSparsePolynomialZonotope)
```

Return the quadratic map of two simple sparse polynomial zonotopes. The quadratic map is the set

$$
    \{x \mid xᵢ = s₁ᵀQᵢs₂, s₁ ∈ S₁, s₂ ∈ S₂, Qᵢ ∈ Q\}.
$$

### Input

  * `Q`  – vector of square matrices
  * `S1` – simple sparse polynomial zonotope
  * `S2` – simple sparse polynomial zonotope

### Output

The quadratic map of the given simple sparse polynomial zonotopes represented as a simple sparse polynomial zonotope.

### Algorithm

This method implements [Kochdumper21a; Proposition 3.1.30](@citet).
