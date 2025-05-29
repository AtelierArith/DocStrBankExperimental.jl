```
overapproximate(X::Intersection{N, <:AbstractZonotope, <:Hyperplane},
                dirs::AbstractDirections) where {N}
```

Overapproximate the intersection between a zonotopic set and a hyperplane with a polyhedron or polytope using the given directions.

### Input

  * `X`    – intersection between a zonotopic set and a hyperplane
  * `dirs` – type of direction representation

### Output

An overapproximation of the intersection between a zonotopic set and a hyperplane. If the directions are bounding, the result is an `HPolytope`, otherwise the result is an `HPolyhedron`.

### Algorithm

This function implements [LeGuernic09; Algorithm 8.1](@citet).
