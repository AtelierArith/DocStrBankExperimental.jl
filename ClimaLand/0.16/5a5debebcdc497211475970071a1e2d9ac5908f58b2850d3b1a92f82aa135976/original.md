```
boundary_var_types(model::AbstractModel{FT}, ::AbstractBC, ::ClimaLand.AbstractBoundary) where {FT}
```

The list of types for additional variables to add to the model auxiliary state, for models solving PDEs, which defaults  to adding a scalar variable on the surface domain  for the top or bottom boundary flux fields, but which can be extended depending on the type of  boundary condition used.

Use in conjunction with `boundary_vars`, in the same way you would use `auxiliary_var_types`. The use of a scalar is appropriate for models with a single PDE; models with multiple PDEs will need to supply multiple scalar fields.
