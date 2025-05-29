```
function forward_pass_NN!(jump, input, output_var, input_vars)
```

Calculates the forward pass through the NN (the output that is produced with the given input). This function can be used when the NN formulation is incorporated into a larger optimization problem.

# Arguments

  * `jump`: JuMP model with the NN formulation
  * `input`: value to be forward passed
  * `output_var`: reference to the NN output variable
  * `input_vars`: references to the NN input variables
