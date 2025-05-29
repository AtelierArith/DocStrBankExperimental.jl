```
DebugFeasibility <: DebugAction
```

Display information about the feasibility of the current iterate

# Fields

  * `atol`:   absolute tolerance for when either equality or inequality constraints are counted as violated
  * `format`: a vector of symbols and string formatting the output
  * `io`:     default stream to print the debug to.

The following symbols are filled with values

  * `:Feasbile` display true or false depending on whether the iterate is feasible
  * `:FeasbileEq` display `=` or `≠` equality constraints are fulfilled or not
  * `:FeasbileInEq` display `≤` or `≰` inequality constraints are fulfilled or not
  * `:NumEq` display the number of equality constraints infeasible
  * `:NumEqNz` display the number of equality constraints infeasible if exists
  * `:NumIneq` display the number of inequality constraints infeasible
  * `:NumIneqNz` display the number of inequality constraints infeasible if exists
  * `:TotalEq` display the sum of how much the equality constraints are violated
  * `:TotalInEq` display the sum of how much the inequality constraints are violated

format to print the output.

# Constructor

DebugFeasibility(     format=["feasible: ", :Feasible];     io::IO=stdout,     atol=1e-13 )
