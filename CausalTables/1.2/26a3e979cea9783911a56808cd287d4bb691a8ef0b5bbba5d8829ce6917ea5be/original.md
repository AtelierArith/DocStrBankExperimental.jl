```
draw_counterfactual(scm::StructuralCausalModel, parents::CausalTable, intervention::Function) -> Vector
```

Generate counterfactual responses based on a given structural causal model (SCM), a table of response parents, and an intervention function. That is, sample the responses that would have occurred had some intervention been applied to the treatment specified by the structural causal model.

# Arguments

  * `scm::StructuralCausalModel`: The structural causal model used to generate counterfactual outcomes.
  * `parents::CausalTable`: A table containing the variables causally preceding the response variable.
  * `intervention::Function`: A function that defines the intervention to be applied to the parent variables. Use `cast_matrix_to_table_function` to convert a function acting on a treatment vector or matrix to a function that acts on a `CausalTable`.

# Returns

A vector of counterfactual responses.
