linear_system_check: return ||Ax-b||_p

`linear_system_check(:: Union{LinearSystem, LLSModel}, :: AbstractState; pnorm :: Real = Inf, kwargs...)`

Note:

  * Returns the p-norm of state.res
  * state.res is filled in if nothing.
