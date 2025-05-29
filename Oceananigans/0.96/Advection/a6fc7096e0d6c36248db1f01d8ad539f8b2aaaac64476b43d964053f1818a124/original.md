```
WENOVectorInvariant(FT = Float64;
                    upwinding = nothing,
                    vorticity_stencil = VelocityStencil(),
                    order = nothing,
                    vorticity_order = nothing,
                    vertical_order = nothing,
                    divergence_order = nothing,
                    kinetic_energy_gradient_order = nothing,
                    multi_dimensional_stencil = false,
                    weno_kw...)
```

Return a vector-invariant weighted essentially non-oscillatory (WENO) scheme. See [`VectorInvariant`](@ref) and [`WENO`](@ref) for kwargs definitions.

If `multi_dimensional_stencil = true` is selected, then a 2D horizontal stencil is implemented for the WENO scheme (instead of a 1D stencil). This 2D horizontal stencil performs a centered 5th-order WENO reconstruction of vorticity, divergence and kinetic energy in the horizontal direction tangential to the upwind direction.
