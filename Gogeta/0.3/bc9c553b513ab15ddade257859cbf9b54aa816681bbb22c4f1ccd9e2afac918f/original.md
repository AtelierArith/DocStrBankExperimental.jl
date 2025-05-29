```
function get_solution(model::JuMP.Model, TE::TEModel)
```

Finds the upper and lower bounds for each input variable given the optimized model.

Returns the bounds for each feature in an array.

# Arguments

  * `model`: The optimized JuMP model.
  * `TE`: Struct of type `TEModel` containing information about the tree ensemble.
