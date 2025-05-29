```
function forward_pass_ICNN!(jump, input, output_var, input_vars)
```

Calculates the forward pass through the ICNN (the output that is produced with the given input). 

# Arguments

  * `jump`: JuMP model with the ICNN
  * `input`: value to be forward passed
  * `output_var`: reference to the ICNN output variable
  * `input_vars`: references to the ICNN input variables
