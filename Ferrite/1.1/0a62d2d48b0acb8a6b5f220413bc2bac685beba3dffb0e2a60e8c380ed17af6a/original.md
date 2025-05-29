```
apply_analytical!(
    a::AbstractVector, dh::AbstractDofHandler, fieldname::Symbol,
    f::Function, cellset=1:getncells(get_grid(dh)))
```

Apply a solution `f(x)` by modifying the values in the degree of freedom vector `a` pertaining to the field `fieldname` for all cells in `cellset`. The function `f(x)` are given the spatial coordinate of the degree of freedom. For scalar fields, `f(x)::Number`, and for vector fields with dimension `dim`, `f(x)::Vec{dim}`.

This function can be used to apply initial conditions for time dependent problems.

!!! note
    This function only works for standard nodal finite element interpolations when the function value at the (algebraic) node is equal to the corresponding degree of freedom value. This holds for e.g. Lagrange and Serendipity interpolations, including sub- and superparametric elements.

