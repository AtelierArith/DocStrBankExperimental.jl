```
NewtonPolygon
```

Representation of a [Newton polygon](https://en.wikipedia.org/wiki/Newton_polygon) of a polynomial.

## Fields

  * `polynomial::P`: the polynomial from which the NewtonPolygon was constructed.
  * `lattices::Vector{SVector{2,Int}}`: the support of the polynomial `p`.
  * `vertices::Vector{Int}`: the vertex indicdes of the Newton polygon.
  * `facets::Vector{SVector{2,Int}}`: the facets of the Newton polygon, i.e. it's convex hull.
  * `subdivision::Vector{SVector{3,Int}}`: the simplices of the regular subdivision of the

Newton polygon
