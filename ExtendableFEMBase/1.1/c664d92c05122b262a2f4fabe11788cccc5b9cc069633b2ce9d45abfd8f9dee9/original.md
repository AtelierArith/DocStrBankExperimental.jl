```
abstract type H1P1TEB{edim} <: AbstractH1FiniteElementWithCoefficients where {edim<:Int}
```

vector-valued (ncomponents = edim) element that uses P1 functions + tangential-weighted edge bubbles as suggested by [Diening, L., Storn, J. & Tscherpel, T., "Fortin operator for the Taylor–Hood element", Num. Math. 150, 671–689 (2022)]

(is inf-sup stable for Stokes if paired with continuous P1 pressure space, less degrees of freedom than MINI)

allowed ElementGeometries:

  * Triangle2D
  * Tetrahedron3D
