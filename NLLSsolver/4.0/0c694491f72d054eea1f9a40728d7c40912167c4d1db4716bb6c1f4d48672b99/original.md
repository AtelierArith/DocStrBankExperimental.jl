```
NLLSsolver.optimize!(problem::NLLSProblem, options=NLLSOptions(), 
                     unfixed=nothing, callback=nullcallback)
```

Optimize the cost defined by `problem`, updating variables in-place, and return  `result::NLLSResult`.

Options such as which optimizer to use and termination criteria can be defined in  options::[`NLLSOptions`](@ref). The default options specify Levenberg-Marquardt optimization.

If not all variables should be optimzed, this can be specified using `unfixed`, which  defines which variables are unfixed, and therefore should be optimized. It can be an integer  index of a single variable, a variable type, or a boolean vector. The default (`nothing`) indicates that all variables should be optimized.

A callback function can be supplied via the `callback` argument. This function is called  after each iteration of the optimization, and should take the following form: `julia     cost, terminate = callback(cost, problem, data::NLLSInternal, iteratedata)``where`cost`is the potentially updated problem cost (if the callback updates the problem),  and`terminate`is an integer, where non-zero values indicate the optimizer should terminate. The value of`terminate`is reported in the result of`optimizer!`. The default,   [`nullcallback`](@ref), does nothing. Existing callbacks [`printoutcallback`](@ref) and  [`storecostscallback`](@ref) print out and store per iteration information respectively.  Callbacks can also be user defined.

Variables are optimized in place, with the `variables` element of `problem::`[`NLLSProblem`](@ref) set to the optimal values found. Other pertinent information, such as the start and end costs, iteration count, high level timings and reasons for termination, is returned in an  [`NLLSResult`](@ref) object.
