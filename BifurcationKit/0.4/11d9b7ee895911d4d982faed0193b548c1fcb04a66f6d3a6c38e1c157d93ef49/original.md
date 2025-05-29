```julia
mutable struct ContState{Tv, T, Teigvals, Teigvec, Tcb} <: BifurcationKit.AbstractContinuationState{Tv}
```

Mutable structure containing the state of the continuation procedure. The fields are meant to change during the continuation procedure. 

!!! danger
    If you mutate these fields yourself, you can break the continuation procedure. Use the methods below to access the fields knowing that they do not yield copies.


# Arguments

  * `z_pred` current solution on the branch
  * `converged` Boolean for newton correction
  * `τ` tangent predictor
  * `z` previous solution
  * `itnewton` Number of newton iteration (in corrector)
  * `step` current continuation step
  * `ds` step size
  * `stopcontinuation` Boolean to stop continuation

# Useful functions

  * `copy(state)` returns a copy of `state`
  * `copyto!(dest, state)`  copy `state` into `dest`
  * `getsolution(state)` returns the current solution (x, p)
  * `gettangent(state)` return the tangent at the current solution
  * `getpredictor(state)` return the predictor at the current solution
  * `getx(state)` returns the x component of the current solution
  * `getp(state)` returns the p component of the current solution
  * `get_previous_solution(state)` returns the previous solution (x, p)
  * `getpreviousx(state)` returns the x component of the previous solution
  * `getpreviousp(state)` returns the p component of the previous solution
  * `is_stable(state)` whether the current state is stable
