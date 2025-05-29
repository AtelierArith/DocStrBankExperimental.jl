```
integrate([func=(u_node,equations)->u_node,] u_ode, semi::AbstractSemidiscretization; normalize=true)
```

Call `func(u_node, equations)` for each vector of nodal variables `u_node` in `u_ode` and integrate the result using a quadrature associated with the semidiscretization `semi`.

If `normalize` is true, the result is divided by the total volume of the computational domain.
