```
create_model(mip_solver, lp_solver, use_direct_model, use_model_names, add_bridges)
```

A `JuMP.Model` extended to be used with SpineOpt. `mip_solver` and `lp_solver` are 'optimizer factories' to be passed to `JuMP.Model` or `JuMP.direct_model`; `use_direct_model` is a `Bool` indicating whether `JuMP.Model` or `JuMP.direct_model` should be used. `use_model_names` is a `Bool` indicating whether the names in the model should be used. `add_bridges` is a `Bool` indicating whether bridges from JuMP to the solver should be added to the model.
