```
function NN_formulate!(jump_model::JuMP.Model, NN_model::Flux.Chain, U_in, L_in; U_bounds=nothing, L_bounds=nothing, U_out=nothing, L_out=nothing, bound_tightening="fast", compress=false, parallel=false, silent=true)
```

Creates a mixed-integer optimization problem from a `Flux.Chain` model.

The parameters are used to specify what kind of bound tightening and compression will be used.

A dummy objective function of 1 is added to the model. The objective is left for the user to define.

# Arguments

  * `jump_model`: The constraints and variables will be saved to this optimization model.
  * `NN_model`: Neural network model to be formulated.
  * `U_in`: Upper bounds for the input variables.
  * `L_in`: Lower bounds for the input variables.

# Optional arguments

  * `bound_tightening`: Mode selection: "fast", "standard", "output" or "precomputed"
  * `compress`: Should the model be simultaneously compressed?
  * `parallel`: Runs bound tightening in parallel. `set_solver!`-function must be defined in the global scope, see documentation or examples.
  * `U_bounds`: Upper bounds. Needed if bound_tightening="precomputed"
  * `L_bounds`: Lower bounds. Needed if bound_tightening="precomputed"
  * `U_out`: Upper bounds for the output variables. Needed if bound_tightening="output".
  * `L_out`: Lower bounds for the output variables. Needed if bound_tightening="output".
  * `silent`: Controls console ouput.
