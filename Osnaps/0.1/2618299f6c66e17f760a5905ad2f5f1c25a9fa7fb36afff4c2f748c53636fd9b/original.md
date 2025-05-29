```
minimize!(o::GenericMinimizer, fn::Function, lb::NTuple{ND}, ub::NTuple{ND}; itmax::Int=210*ND, dmax::Real=1e-7, avgtimes::Int=1)
```

An interface function to proceed the "global" minimization.

## Arguments:

  * `o`:        An object for the minimization created by `minimizer(..., method="global")`.
  * `fn`:       Objective function to be minimized.              `fn` should be callable with only one argument of `fn(x::Vector)`.              If you have any additional arguments need to pass into it,              dispatch the function by `fcall(fn, x) = fn(x; kwargs...)`
  * `lb`:       Lower bounds of minimization which are forced to be feasible.
  * `ub`:       Upper bounds of minimization which are forced to be feasible.
  * `itmax`:    Maximum of minimizing iteration (*optional*).
  * `dmax`:     An Euclidean distance acts as a criterion to             prevent the population falling into local minimal (*optional*).
  * `avgtimes`: Number of average times of the whole minimization process (*optional*).
