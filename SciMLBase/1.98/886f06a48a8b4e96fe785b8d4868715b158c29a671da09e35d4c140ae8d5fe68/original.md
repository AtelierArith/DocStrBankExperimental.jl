```
SecondOrderDDEProblem{isinplace}(f,du0,u0,h,tspan,p=NullParameters(),callback=CallbackSet())
```

Define a second order DDE problem with the specified function.

# Arguments

  * `f`: The function for the second derivative.
  * `du0`: The initial derivative.
  * `u0`: The initial condition.
  * `h`: The initial history function.
  * `tspan`: The timespan for the problem.
  * `p`: Parameter values for `f`.
  * `callback`: A callback to be applied to every solver which uses the problem. Defaults to nothing.

`isinplace` optionally sets whether the function is inplace or not. This is determined automatically, but not inferred.
