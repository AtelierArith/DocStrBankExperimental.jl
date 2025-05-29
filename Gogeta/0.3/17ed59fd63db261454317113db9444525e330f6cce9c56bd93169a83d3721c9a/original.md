```
function NN_formulate_Psplit!(jump_model::JuMP.Model, NN_model::Flux.Chain, P, U_in, L_in; silent=true)
```

Creates an optimization problem from a `Flux.Chain` model using P-split formulation for the disjunctive constraints.

The parameter P specifies the number of splits

A dummy objective function of 1 is added to the model. The objective is left for the user to define.

# Arguments

  * `jump_model`: The constraints and variables will be saved to this optimization model.
  * `NN_model`: Neural network model to be formulated.
  * `P`: The number of splits
  * `U_in`: Upper bounds for the input variables.
  * `L_in`: Lower bounds for the input variables.

# Optional arguments

  * `strategy`: Controls the partioning strategy. Available options are `equalsize` (default), `equalrange`, `random`, `snake`
  * `bound_tightening`: How the bounds for neurons are produced. Available options are `fast`(default), `standard`, `precomputed`
  * `parallel`: Is used in standard bounding, for speeding up the formulation default is `false`
  * `U_bounds`, `L_bounds`: Upper and lower bounds used in only for `precomputed` bound-tightening.
  * `silent`: Controls console ouput. Default is true.
