```
abstract type H1BUBBLE{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

Piecewise bubbles (=zero at boundary)

allowed element geometries:

  * Edge1D (one quadratic bubble)
  * Triangle2D (one cubic bubble)
  * Quadrilateral2D (one quartic bubble)
  * Tetrahedron3D (one cubic bubble)
