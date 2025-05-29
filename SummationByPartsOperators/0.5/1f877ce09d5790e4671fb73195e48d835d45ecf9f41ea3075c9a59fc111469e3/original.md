```
couple_discontinuously(D, mesh, [coupling=Val(:central)])
```

Return a derivative operator corresponding to a discontinuous coupling of `D` on the cells of the given `mesh` as in (nodal) discontinuous Galerkin (CG) methods. If the underlying SBP operators are [`LegendreDerivativeOperator`](@ref)s, these are DG spectral element methods (DGSEM). However, a discontinuous coupling of arbitrary SBP operators is supported.

The `mesh` can be a [`UniformMesh1D`](@ref) or a [`UniformPeriodicMesh1D`](@ref). The `coupling` can be

  * `Val(:central)` (default), resulting in classical SBP properties
  * `Val(:minus)` or `Val(:plus)`, resulting in upwind SBP operators

## References

  * Ranocha, Mitsotakis, Ketcheson (2021). A Broad Class of Conservative Numerical Methods for Dispersive Wave Equations. [DOI: 10.4208/cicp.OA-2020-0119](https://doi.org/10.4208/cicp.OA-2020-0119)
