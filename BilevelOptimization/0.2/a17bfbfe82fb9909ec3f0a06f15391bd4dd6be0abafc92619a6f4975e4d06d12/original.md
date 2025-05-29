```
`build_blp_model(bp::BilevelLP, solver; [comp_method])`
```

Build a JuMP model (constraints and objective) based on the data from bp and with a solver.

Returns a tuple `(m, x, y, λ, s)`.

An optional keyword `comp_method` can be passed for handling complementarity constraints, default is `SOS1Complementarity`.
