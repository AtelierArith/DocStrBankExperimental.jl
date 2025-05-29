```
couple_continuously(D, mesh)
```

Return a derivative operator corresponding to a continuous coupling of `D` on the cells of the given `mesh` as in (nodal) continuous Galerkin (CG) methods. If the underlying SBP operators are [`LegendreDerivativeOperator`](@ref)s, these are CG spectral element methods (CGSEM). However, a continuous coupling of arbitrary SBP operators is supported.

The `mesh` can be a [`UniformMesh1D`](@ref) or a [`UniformPeriodicMesh1D`](@ref).

## References

  * Ranocha, Mitsotakis, Ketcheson (2021). A Broad Class of Conservative Numerical Methods for Dispersive Wave Equations. [DOI: 10.4208/cicp.OA-2020-0119](https://doi.org/10.4208/cicp.OA-2020-0119)
