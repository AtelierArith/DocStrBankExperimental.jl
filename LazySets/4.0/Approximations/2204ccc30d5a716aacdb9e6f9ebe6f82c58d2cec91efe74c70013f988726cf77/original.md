```
overapproximate(P::DensePolynomialZonotope, ::Type{<:Zonotope})
```

Overapproximate a polynomial zonotope with a zonotope.

### Input

  * `P`        – polynomial zonotope
  * `Zonotope` – target set type

### Output

A zonotope.

### Algorithm

This method implements [Althoff13; Proposition 1](@citet).
