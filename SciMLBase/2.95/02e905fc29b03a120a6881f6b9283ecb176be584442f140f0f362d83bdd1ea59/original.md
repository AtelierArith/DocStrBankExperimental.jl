```
DynamicalDDEProblem{isinplace}(f1,f2,v0,u0,h,tspan,p=NullParameters(),callback=CallbackSet())
```

Define a dynamical DDE problem from the two functions `f1` and `f2`.

# Arguments

  * `f1` and `f2`: The functions in the DDE.
  * `v0` and `u0`: The initial conditions.
  * `h`: The initial history function.
  * `tspan`: The timespan for the problem.
  * `p`: Parameter values for `f1` and `f2`.
  * `callback`: A callback to be applied to every solver which uses the problem. Defaults to nothing.

`isinplace` optionally sets whether the function is inplace or not. This is determined automatically, but not inferred.
