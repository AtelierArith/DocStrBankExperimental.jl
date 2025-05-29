```
BoundaryConditions{L<:Union{<:Dirichlet, <:Neumann},R<:Union{<:Dirichlet, <:Neumann},M<:Robin}
```

The boundary conditions for the `MBProblem`.

# Fields

  * `lhs::L`: The left-hand side boundary condition. Must be `Dirichlet` or `Neumann`.
  * `rhs::R`: The right-hand side boundary condition. Must be `Dirichlet` or `Neumann`.
  * `moving_boundary::M`: The moving boundary condition. Must be `Robin`.

See also [`Dirichlet`](@ref), [`Neumann`](@ref), and [`Robin`](@ref) for the types of  boundary conditions you can construct.
