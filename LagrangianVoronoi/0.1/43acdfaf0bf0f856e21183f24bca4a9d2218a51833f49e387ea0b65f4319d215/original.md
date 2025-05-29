```
bdary_friction!(grid::VoronoiGrid, vDirichlet::Function, dt::Float64)
```

Applies a viscous drag at boundaries. This is used for Dirichlet condition for velocity when the the velocity is tangent of the surface. It cannot be used for inflows or outflows. The function `vDirichlet` should accept a single argument `x::RealVector` and return a `RealVector` corresponding to the velocity of the boundary.
