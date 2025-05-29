```
L2Projector(grid::AbstractGrid)
```

Initiate an `L2Projector` for projecting quadrature data onto a function space. To define the function space, add interpolations for different cell sets with `add!` before `close!`ing the projector, see the example below.

The `L2Projector` acts as the integrated left hand side of the projection equation: Find projection $u \in U_h(\Omega) \subset L_2(\Omega)$ such that

$$
\int v u \ \mathrm{d}\Omega = \int v f \ \mathrm{d}\Omega \quad \forall v \in U_h(\Omega),
$$

where $f \in L_2(\Omega)$ is the data to project. The function space $U_h(\Omega)$ is the finite element approximation given by the interpolations `add!`ed to the `L2Projector`.

### Example

```julia
proj = L2Projector(grid)
qr_quad = QuadratureRule{RefQuadrilateral}(2)
add!(proj, quad_set, Lagrange{RefQuadrilateral, 1}(); qr_rhs = qr_quad)
qr_tria = QuadratureRule{RefTriangle}(1)
add!(proj, tria_set, Lagrange{RefTriangle, 1}(); qr_rhs = qr_tria)
close!(proj)

vals = Dict{Int, Vector{Float64}}() # Can also be Vector{Vector},
                                    # indexed with cellnr
for (set, qr) in ((quad_set, qr_quad), (tria_set, qr_tria))
    nqp = getnquadpoints(qr)
    for cellnr in set
        vals[cellnr] = rand(nqp)
    end
end

projected = project(proj, vals)
```

where `projected` can be used in e.g. `evaluate_at_points` with the [`PointEvalHandler`](@ref), or with [`evaluate_at_grid_nodes`](@ref).
