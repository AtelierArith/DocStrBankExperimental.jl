```
boundary_var_domain_names(::AbstractBC, ::ClimaLand.AbstractBoundary)
```

The list of domain names for additional variables to add to the model auxiliary state, for models solving PDEs, which defaults  to adding storage on the surface domain  for the top or bottom boundary flux fields, but which can be extended depending on the type of  boundary condition used.

Use in conjunction with `boundary_vars`, in the same way you would use `auxiliary_var_domain_names`. 
