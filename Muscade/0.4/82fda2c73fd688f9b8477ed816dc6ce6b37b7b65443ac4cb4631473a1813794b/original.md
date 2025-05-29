```
solve(Solver;dbg=(;),verbose=true,silenterror=false,kwargs...)
```

Execute an analysis using `Solver`, and safeguard partial results in the case of error. 

# Named arguments

  * `dbg=(;)`           a named tuple to trace the call tree (for debugging)
  * `verbose=true`      set to false to suppress printed output (for testing)
  * `silenterror=false` set to true to suppress print out of error (for testing)
  * `kwargs...`         Further arguments passed on to the method `solve` provided by the solver

This will call the method `solve` provided by the solver with `solve(Solver,pstate,verbose,(dbg...,solver=Symbol(Solver));kwargs...)`

See also: [`SweepX`](@ref), [`DirectXUA`](@ref), [`initialize!`](@ref) 
