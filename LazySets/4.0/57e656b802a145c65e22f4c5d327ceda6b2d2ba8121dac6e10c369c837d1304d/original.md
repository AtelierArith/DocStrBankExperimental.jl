```
constrained_dimensions(P::AbstractPolyhedron)
```

Return the indices in which a polyhedron is constrained.

### Input

  * `P` – polyhedron

### Output

A vector of ascending indices `i` such that the polyhedron is constrained in dimension `i`.

### Examples

A 2D polyhedron with constraint $x1 ≥ 0$ is constrained in dimension 1 only.
