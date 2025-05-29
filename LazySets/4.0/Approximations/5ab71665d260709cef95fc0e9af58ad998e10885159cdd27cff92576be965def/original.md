```
overapproximate(P::SparsePolynomialZonotope{N}, ::Type{<:VPolytope}) where {N}
```

Overapproximate a sparse polynomial zonotope with a polytope in vertex representation.

### Input

  * `P`         – sparse polynomial zonotope
  * `VPolytope` – target type

### Output

A `VPolytope`.

### Algorithm

This method implements [Kochdumper21a; Proposition 3.1.15](@citet). The idea is to split `P` into a linear and nonlinear part (such that `P = P₁ ⊕ P₂`). The nonlinear part is enclosed by a zonotope. Then we combine the vertices of both sets and finally apply a convex-hull algorithm.
