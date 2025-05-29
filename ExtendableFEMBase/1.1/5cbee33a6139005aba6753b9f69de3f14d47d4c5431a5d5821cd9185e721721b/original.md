```
abstract type H1MINI{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

Mini finite element.

allowed element geometries:

  * Triangle2D (linear polynomials + cubic cell bubble)
  * Quadrilateral2D (Q1 space + quartic cell bubble)
  * Tetrahedron3D (linear polynomials + cubic cell bubble)
