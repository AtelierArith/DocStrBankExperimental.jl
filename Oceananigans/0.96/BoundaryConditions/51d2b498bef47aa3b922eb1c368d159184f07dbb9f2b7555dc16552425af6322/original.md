```
BoundaryCondition(classification::AbstractBoundaryConditionClassification, condition::Function;
                  parameters = nothing,
                  discrete_form = false,
                  field_dependencies=())
```

Construct a boundary condition of type `classification` with a function boundary `condition`.

By default, the function boudnary `condition` is assumed to have the 'continuous form' `condition(ξ, η, t)`, where `t` is time and `ξ` and `η` vary along the boundary. In particular:

  * On `x`-boundaries, `condition(y, z, t)`.
  * On `y`-boundaries, `condition(x, z, t)`.
  * On `z`-boundaries, `condition(x, y, t)`.

If `parameters` is not `nothing`, then function boundary conditions have the form `func(ξ, η, t, parameters)`, where `ξ` and `η` are spatial coordinates varying along the boundary as explained above.

If `discrete_form = true`, the function `condition` is assumed to have the "discrete form",

```
condition(i, j, grid, clock, model_fields)
```

where `i`, and `j` are indices that vary along the boundary. If `discrete_form = true` and `parameters` is not `nothing`, the function `condition` is called with

```
condition(i, j, grid, clock, model_fields, parameters)
```
