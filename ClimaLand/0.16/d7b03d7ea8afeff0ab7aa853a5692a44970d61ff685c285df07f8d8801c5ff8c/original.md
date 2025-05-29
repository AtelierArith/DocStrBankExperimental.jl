```
boundary_flux!(bc_field, bc::AbstractBC, bound_type::AbstractBoundary, Δz, _...)
```

A function which updates bc_field with the correct boundary flux  given any boundary condition (BC). 
