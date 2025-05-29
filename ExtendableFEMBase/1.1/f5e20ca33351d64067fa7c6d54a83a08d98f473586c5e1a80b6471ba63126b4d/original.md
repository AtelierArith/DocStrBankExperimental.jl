```
abstract type HDIVRTkENRICH{k,edim} <: AbstractHdivFiniteElement where {edim<:Int}
```

Internal (normal-zero) Hdiv-conforming vector-valued (ncomponents = edim) Raviart-Thomas space of order k ≥ 1 with the additional orthogonality property that their divergences are L2-orthogonal on P_{k-edim+1}. Example: HDIVRTkENRICH{1,2} gives the edim interior RT1 bubbles (= normal-trace-free) on a triangle, their divergences have integral mean zero; HDIVRTkENRICH{2,2} gives three RT2 bubbles on a triangle whose divergences are L2-orthogonal onto all P1 functions. The maximal order for k is 4 on a Triangle2D (edim = 2) and 3 on Tetrahedron3D (edim = 3). These spaces have no approximation power on their own, but can be used as enrichment spaces in divergence-free schemes for incompressible Stokes problems.

allowed ElementGeometries:

  * Triangle2D
  * Tetrahedron3D
