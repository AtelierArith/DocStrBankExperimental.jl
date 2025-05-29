```
function NN_incorporate!(
    jump_original::JuMP.Model,
    param_source,
    output_var,
    input_vars...;
    U_in,
    L_in,
    compress=false,
    bound_tightening="fast",
    parallel=false,
    U_out=nothing,
    L_out=nothing
)
```

Formulates the neural network (NN) as a MIP into a JuMP model. The model parameters must be contained in a JSON file located at the given filepath OR in a Flux.Chain model.

JSON file structure:

  * Parameter sets must be named based on the layer type  - "FCx" where 'x' indicates the layer number.
  * 'FC' indicates a fully connected layer. These parameter sets contain weights and biases.
  * For a clear example on how to export these parameters from Tensorflow, see examples/-folder of the package repository

This function modifies the JuMP model given as input. The input and output variable references that are given as input to this function will be linked to the appropriate variables in the NN formulation. No additional names are added to the JuMP model - all variables are added as anonymous. 

Different bound tightening modes and compression can be used. To use bound tightening modes other than "fast", `set_solver!`-function must be defined in the global scope which defines the solver and other necessary for the JuMP model used in bound tightening.

# Arguments

  * `jump_original`: JuMP model into which the neural network MIP should be incorporated
  * `param_source`: relative path to the JSON file containing the model parameters OR a Flux.Chain model
  * `output_var`: reference to the variable that should be linked to the NN output
  * `input_vars`: references to the variables that will be used as the NN inputs

# Keyword Arguments

  * `U_in`: vector of upper bounds for the input variables
  * `L_in`: vector of lower bounds for the input variables
  * `compress`: reduce NN size by removing stable and linearly dependent neurons
  * `bound_tightening`: which bound tightening mode to use: "fast", "standard", "output"
  * `parallel`: use multiprocessing for bound tightening
  * `silent`: suppress console output
  * `U_out`: vector of upper bounds for the output variables - necessary when output bound tightening is used
  * `L_out`: vector of lower bounds for the output variables - necessary when output bound tightening is used
