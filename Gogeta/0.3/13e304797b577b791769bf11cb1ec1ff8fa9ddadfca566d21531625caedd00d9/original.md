```
function tree_callback_algorithm(cb_data, TE::TEModel, opt_model::JuMP.Model)
```

The callback algorithm for tree ensemble optimization using lazy constraints.

Using lazy constraints, the split constraints are added one-by-one for each tree.

See examples or documentation for information on how to use lazy constraints.

# Arguments

  * `cb_data`: Callback data
  * `TE`: A tree ensemble model in the universal data type `TEModel`.
  * `opt_model`: A JuMP model containing the formulation.
