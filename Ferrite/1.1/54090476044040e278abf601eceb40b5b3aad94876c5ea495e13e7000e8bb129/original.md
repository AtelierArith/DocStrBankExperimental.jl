```
project(proj::L2Projector, vals, [qr_rhs::QuadratureRule])
```

Makes a L2 projection of data `vals` to the nodes of the grid using the projector `proj` (see [`L2Projector`](@ref)).

`project` integrates the right hand side, and solves the projection $u$ from the following projection equation: Find projection $u \in U_h(\Omega) \subset L_2(\Omega)$ such that

$$
\int v u \ \mathrm{d}\Omega = \int v f \ \mathrm{d}\Omega \quad \forall v \in U_h(\Omega),
$$

where $f \in L_2(\Omega)$ is the data to project. The function space $U_h(\Omega)$ is the finite element approximation given by the interpolations in `proj`.

The data `vals` should be an `AbstractVector` or `AbstractDict` that is indexed by the cell number. Each index in `vals` should give an `AbstractVector` with one element for each cell quadrature point.

If `proj` was created by calling `L2Projector(ip, grid, set)`, `qr_rhs` must be given. Otherwise, this is added for each domain when calling `add!(proj, args...)`.

Alternatively, `vals` can be a matrix, with the column index referring the cell number, and the row index corresponding to quadrature point number. Example (scalar) input data:

```julia
vals = [
    [0.44, 0.98, 0.32], # data for quadrature point 1, 2, 3 of element 1
    [0.29, 0.48, 0.55], # data for quadrature point 1, 2, 3 of element 2
    # ...
]
```

or equivalent in matrix form:

```julia
vals = [
    0.44 0.29 # ...
    0.98 0.48 # ...
    0.32 0.55 # ...
]
```

Supported data types to project are `Number`s and `AbstractTensor`s.

!!! note
    The order of the returned data correspond to the order of the `L2Projector`'s internal `DofHandler`. The data can be further analyzed with [`evaluate_at_points`](@ref) and [`evaluate_at_grid_nodes`](@ref). Use [`write_projection`](@ref) to export the result.

