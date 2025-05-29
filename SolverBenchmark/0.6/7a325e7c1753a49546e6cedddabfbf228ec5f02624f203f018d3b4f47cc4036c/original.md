```
bmark_solvers(solvers :: Dict{Symbol,Any}, args...; kwargs...)
```

Run a set of solvers on a set of problems.

#### Arguments

  * `solvers`: a dictionary of solvers to which each problem should be passed
  * other positional arguments accepted by `solve_problems`, except for a solver name

#### Keyword arguments

Any keyword argument accepted by `solve_problems`

#### Return value

A Dict{Symbol, AbstractExecutionStats} of statistics.
