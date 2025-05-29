```
abstract type H1P1TEB{edim} <: AbstractH1FiniteElementWithCoefficients where {edim<:Int}
```

vector-valued (ncomponents = edim) element that uses P1 functions + tangential-weighted edge bubbles as suggested by ["Fortin Operator for the Taylor-Hood Element", 2021, arxiv:2104.13953]

(is inf-sup stable for Stokes if paired with continuous P1 pressure space, less degrees of freedom than MINI)

allowed ElementGeometries:

  * Triangle2D
  * Tetrahedron3D
