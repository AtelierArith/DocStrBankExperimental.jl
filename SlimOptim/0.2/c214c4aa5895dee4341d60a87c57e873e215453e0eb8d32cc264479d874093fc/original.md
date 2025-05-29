```
linesearch(ls, sol, d, f, g!, fg!, t, funRef, gtd, gvec)
```

Line search interface to LineSearches.jl

# Arguments

  * `ls`: Line search structure (see LineSearches.jl documentation)
  * `f`: Objective function, x -> f(x)
  * `g!``: Gradient in place function, x-> (g.= gradient(x))
  * `fg!``: Objective and in place gradient function, x-> (f = f(x); g.= gradient(x))
  * `t`: Initial steplength gess
  * `funRef`: Reference objective function value
  * `gtd`: Reference direction inner product dot(g0, d0)
  * `gvec`: prealocated array for thhe gradient
