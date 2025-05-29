```
function ICNN_incorporate!(jump::JuMP.Model, filepath::String, output_var, input_vars...)
```

Incorporates the input convex neural network (ICNN) as an LP into a JuMP model. The model parameters must be contained in a JSON file located in the given filepath. For more information about ICNNs see Amos et al. (2017).

JSON file structure:

  * Parameter sets must be named based on the layer type  - either "FCx" or "SKIPx" where 'x' indicates the layer number.
  * 'FC' indicates a fully connected layer. These parameter sets contain weights and biases.
  * 'SKIP' indicates a skip connection layer. These only contain weights.
  * For a clear example on how to export these parameters from Tensorflow, see examples/-folder of the package repository

This function modifies the JuMP model given as input. The input and output variable references that are given as input to this function will be linked to the appropriate variables in the ICNN formulation. No additional names are added to the JuMP model - all variables are added as anonymous. Also the JuMP model objective function is modified to include the ICNN output as a penalty term.

# Arguments

  * `jump`: JuMP model where the LP formulation should be incorporated
  * `filepath`: relative path to the JSON file containing the model parameters
  * `output_var`: reference to the variable that should be linked to the ICNN output
  * `input_vars`: references to the variables that will be used as the ICNN inputs
