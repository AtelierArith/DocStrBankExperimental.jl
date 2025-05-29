```
function TE_formulate!(opt_model::JuMP.Model, TE::TEModel, objective)
```

Formulates a tree ensemble to the JuMP model `opt_model` based on the given tree ensemble `TE`.

The JuMP model is formulated without the split constraints.

An objective function either minimizing or maximizing the ensemble output is added to the `JuMP` model.

# Arguments

  * `opt_model`: A `JuMP` model where the formulation will be saved to.
  * `TE`: A tree ensemble model in the universal data type `TEModel`.
  * `objective`: MIN*SENSE or MAX*SENSE. Minimize or maximize the tree ensemble output.
