```
get_solution(m::Model, modelvars::OrderedDict, vardata::VariableData)::Tuple{OrderedDict{Int,Int},MOI.TerminationStatusCode}
```

Return a solution and status code after solving the given model `m` and using model variables `modelvars` and variable data `vardata` to access the solution values.

# Notes

  * Model is optimally solved only if the status code is [`MOI.OPTIMAL`](https://jump.dev/JuMP.jl/stable/moi/reference/models/#MathOptInterface.TerminationStatusCode).
  * Solution is a mapping from variable to its value (both as ints).
