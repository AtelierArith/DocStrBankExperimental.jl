```
function check_ICNN(optimizer, filepath, output_value, input_values...; show_output=true, negated=false)
```

Verifies that the output of an ICNN contained in a larger optimization problem formulation is correct.  Verification is needed because the ICNN LP formulation cannot detect infeasibility.

Returns true if ICNN output is correct and false otherwise.

# Arguments

  * `optimizer`: JuMP optimizer object
  * `filepath`: relative path to the JSON file containing the model parameters
  * `output_value`: ICNN output in the optimal solution of the larger optimization problem
  * `input_values`: the values of the ICNN inputs at the optimal solution of the larger optimization problem

# Keyword Arguments

  * `show_output`: print additional information to the console
  * `negated`: set 'true' if the ICNN has been trained with the data negated
