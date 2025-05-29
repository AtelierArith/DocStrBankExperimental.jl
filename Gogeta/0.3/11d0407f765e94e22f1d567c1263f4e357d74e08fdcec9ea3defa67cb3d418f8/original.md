```
function add_split_constraints!(opt_model::JuMP.Model, TE::TEModel)
```

Adds all split constraints to the formulation.

# Arguments

  * `opt_model`: A JuMP model containing the formulation.
  * `TE`: A tree ensemble model in the universal data type `TEModel`.
