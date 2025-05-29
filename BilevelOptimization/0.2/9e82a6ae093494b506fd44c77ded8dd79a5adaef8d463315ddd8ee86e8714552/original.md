```
`build_blp_model(m::JuMP.Model, bp::BilevelLP, x, y; [comp_method])`
```

Adds the lower-level constraints and optimality conditions to an existing JuMP model. This assumes the upper-level feasibility constraints and objective have already been set.

Returns a tuple `(m, x, y, λ, s)`.

An optional keyword `comp_method` can be passed for handling complementarity constraints, default is `SOS1Complementarity`.
