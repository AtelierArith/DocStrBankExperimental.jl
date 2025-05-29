```julia
tri_quadrature(deg; vertices, transform)

```

Calculate quadrature points in a triangle

@arg deg: polynomial degree @arg vertices: vertex coordinates

  * for a equilateral triangle, the vertices are ([-1.0, -1 / √3], [1.0, -1 / √3], [0.0, 2 / √3])
  * for a right triangle, the vertices take ([-1.0, -1.0], [1.0, -1.0], [-1.0, 1.0])

@arg if transform equals to true, then we transform the coordinates from x-y to r-s plane
