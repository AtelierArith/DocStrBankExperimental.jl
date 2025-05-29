```
abstract type H1BR{edim} <: AbstractH1FiniteElementWithCoefficients where {edim<:Int}
```

vector-valued (ncomponents = edim) Bernardi–Raugel element (first-order polynomials + normal-weighted face bubbles)

allowed ElementGeometries:

  * Triangle2D (piecewise linear + normal-weighted face bubbles)
  * Quadrilateral2D (Q1 space + normal-weighted face bubbles)
  * Tetrahedron3D (piecewise linear + normal-weighted face bubbles)
